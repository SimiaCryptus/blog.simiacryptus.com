{
  "disqus_url": "http://blog.simiacryptus.com/blog/gpuaccelerated_neural_networks_with_cudnn/",
  "disqus_title": "GPU-accelerated neural networks with CuDNN",
  "Title": "GPU-accelerated neural networks with CuDNN",
  "Pubdate": "2017-08-02",
  "Keywords": [
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "gpuaccelerated_neural_networks_with_cudnn",
  "Section": "post",
  "comments": true
}

A recent project that has huge implications for the field of AI is NVidia’s CuDNN library and related cuda-based libraries. Beyond simply being very useful and enabling hardware accelerated AI with cutting-edge performance, it establishes a common layer of high-performance mathematical primitives that, while using the hardware to its best extent, provides a common api to write software. With my recent addition of CuDNN-based layers, Mindseye should behave comparably with any other state-of-the-art deep learning library. In a more general sense, I think this will abstract away an important layer of problems, allowing AI software development to focus on solving higher-level problems.

The initial integration of CuDNN was completed over the course of three phases, and improved the performance of CNN evaluation and training by about 10x over the previous Aparapi-accelerated implementation. At this level of integration, nearly all of the computational load is being handled by the CuDNN library on the GPU, and we can rest assured we are working with state-of-the-art performance. Full integration was developed over three phases, each of which approximately doubled performance.

In the first phase we integrated the 2d convolution operator, alone, into our code as a new type of layer based closely on the Aparapi convolution layer. This meant that we send the input and weight array from host (CPU) memory to the device, then executed the convolution on their device, and finally reading the result from device memory back to host memory.  I expected a performance gain relative to the Aparapi/OpenCL implementation we were using previously, if for no other reason than CuDNN provides a range of convolution algorithms and logic to intelligently choose between them. The Previous Aparapi layer used a single, fairly naive algorithm. This new, CuDNN-powered convolution proved to be approximately twice as fast during informal testing. I was actually somewhat surprised that code written in pure Java, compiled via Aparapi and OpenCL, could come so close to NVidia’s expertly developed native CUDA code.

Performance analysis of the results showed that we were actually spending a large amount of time transferring memory between the host and device, resulting in a bottleneck. This was due fundamentally because we were only executing individual layers on the GPU, not entire networks. If our network had 100 layers, we would have to move intermediate results back and forth 100 times per network run. The solution is to make the data objects understand “where” they are while being passed between layers, and add logic to minimize transfers. Data already on the GPU could be then re-used in downstream layers or on backpropagation passes. However this strategy also requires we add implementations of many other layers from CuDNN, so that we can use these additional layer types to operate on GPU memory. Otherwise, we’d have to do just as much memory transfer in order to perform our pure-java activation layer, for example. Informal testing when this feature was completed improved performance another 2 to 3-fold. This also required changes to how networks were evaluated by limiting execution batch sizes in order to manage GPU memory resources. Unfortunately, due to Aparapi’s simple API, this type of optimization does not appear possible within that framework. 

So far, we’ve achieved a 5x performance increase. The next boost came when testing an alternate implementation of the layers which used 32-bit floating point numbers instead of the 64-bit double precision float use in the pure-Java code. Although floating point layers and networks cannot mix efficiently with with double precision layers, when used consistently we saw CNN performance increase another two-fold. Despite the loss in precision, training results do not appear affected.

All in all, we gained an entire order of magnitude in the performance of this network. At this point, the performance of other components such as the L-BFGS algorithm start to become more relevant to performance. Additionally, the more direct and powerful cuda and CuDNN apis make multi-GPU support possible. I found the CuDNN library to be very easy to use, and I think that by providing a common high-performance runtime for neural networks, they have enabled an entirely new generation of AI tools that can concentrate on the next-higher-level problems. As such, I think this is one of the more important recent developments in the field of AI.
