{
  "disqus_url": "http://blog.simiacryptus.com/blog/the_2d_convolution_a_layer_development_story/",
  "disqus_title": "The 2D Convolution: A Layer Development Story",
  "Title": "The 2D Convolution: A Layer Development Story",
  "Pubdate": "2018-02-22",
  "Keywords": [
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "the_2d_convolution_a_layer_development_story",
  "Section": "post",
  "comments": true
}

Hello! Today we will be discussing many aspects of developing differentiable network layers in MindsEye as we explore the 2d convolution layer and its various implementations. First, for background, see my previous post about [Test Driven Development with neural networks](http://blog.simiacryptus.com/2017/12/unit-testing-and-neural-networks.html). Given these test facilities and perhaps more elemental layers, we need to construct a convolution layer that will work in large modern networks with large images as input.

Our first goal is to code a [reference implementation](https://github.com/SimiaCryptus/MindsEye/blob/5824ce862983c4b565326af9c5ee6686f327421e/src/main/java/com/simiacryptus/mindseye/layers/java/FullyConnectedReferenceLayer.java), generally in pure java. The code should be reasonably efficient, but the main goal here is clarity of implementation. This implementation captures what the layer does in a clear way, whose validity is demonstrated by the [testing code](https://github.com/SimiaCryptus/MindsEye/blob/5824ce862983c4b565326af9c5ee6686f327421e/src/test/java/com/simiacryptus/mindseye/layers/java/FullyConnectedReferenceLayerTest.java). Once it is complete, we can use it in testing new implementations to ensure the behavior is not only valid but also correct.

More efficient implementations can take a variety of routes. You might call native libraries, such as [BLAS](https://github.com/SimiaCryptus/MindsEye/blob/5824ce862983c4b565326af9c5ee6686f327421e/src/main/java/com/simiacryptus/mindseye/layers/java/FullyConnectedLayer.java#L161) or [CuDNN](https://github.com/SimiaCryptus/MindsEye/tree/5824ce862983c4b565326af9c5ee6686f327421e/src/main/java/com/simiacryptus/mindseye/layers/cudnn). Another route for layers that are well suited to GPU acceleration, such as convolution, is to write directly for the GPU. There are a couple of ways to do this from Java. The first is to write custom CUDA kernels, which then execute natively on the GPU. This is essentially what CuDNN is, as far as I can tell. Another way is through a project called [Aparapi](http://aparapi.com/), which trans-compiles pure java into OpenCL source code, which then runs on either the CPU or GPU. This provides a very flexible and portable route for compute acceleration, though it has some significant performance limitations currently.

In MindsEye, we have convolution implementations built using both [CuDNN](https://github.com/SimiaCryptus/MindsEye/blob/5824ce862983c4b565326af9c5ee6686f327421e/src/main/java/com/simiacryptus/mindseye/layers/cudnn/ConvolutionLayer.java) and [Aparapi](https://github.com/SimiaCryptus/MindsEye/blob/5824ce862983c4b565326af9c5ee6686f327421e/src/main/java/com/simiacryptus/mindseye/layers/aparapi/ConvolutionLayer.java). The CuDNN is highly preferred if the CuDNN library is available. Both implementations, however, have some significant limitations. Most importantly, they will not work if the input or kernel dimensions are beyond a certain size. This makes sense when you consider how easily these tensors can fill hundreds of megabytes of memory, that the basic compute unit would only scale so big. How do we address that, though, so we can use modern networks with modern images?

As usual, to achieve scalability we mainly need to identify and implement a partitioning strategy. Divide and conquer. If we are faced with a 1024x1024 input image and a 1024-band 3x3 convolution, how can break down the problem? We can process the image in tiles, so that each tile (slightly overlapping) is then processed individually by the network. Now we have a 128x128 input image, but our 1024-band convolution is still too big. It is a little less obvious, but the kernel can be broken into tiles as well, in the same way a large matrix-vector multiplication [can be broken down](https://en.wikipedia.org/wiki/Matrix_multiplication_algorithm#Shared-memory_parallelism). Thus, a single execution would partition into 64 128x128 image tiles, and 64 128-band convolutions, for around 4096 elemental convolution operations.On the bright side, this opens up a great opportunity for distributing load over multiple GPUs. (I have developed this code using 2 heterogeneous GPUs, both supporting the [CUDA 6 / Pascal](https://devblogs.nvidia.com/unified-memory-cuda-beginners/) managed-memory architecture.)

Accomplishing this high scale support brings up my final point on layer development... We’ve discussed how layers can be implemented from scratch, or assembled into networks which can then themselves be treated as layers in a deeply nested structure. [Layers](https://github.com/SimiaCryptus/MindsEye/blob/5824ce862983c4b565326af9c5ee6686f327421e/src/main/java/com/simiacryptus/mindseye/layers/cudnn/ImgTileSubnetLayer.java#L104) can also construct networks or other layers dynamically, or at evaluation time. Our network does not know beforehand, about what image size will be passed to it, nor will it need to. At evaluation time, the top-level convolution class sees that the image size is over a threshold, and then generates the needed select-process-reassemble network just before it is evaluated.

Layers and networks may be executed by conventional computer code, but they represent application code themselves of an entirely different nature. To construct this new type of software, we will need new software development tools and patterns beyond just numerical optimization.

