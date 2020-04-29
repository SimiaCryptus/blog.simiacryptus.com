{
  "disqus_url": "http://blog.simiacryptus.com/blog/what_is_the_value_of_a_human_life/",
  "disqus_title": "What is the value of a human life?",
  "Title": "What is the value of a human life?",
  "Pubdate": "2017-05-21",
  "Keywords": [
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "what_is_the_value_of_a_human_life",
  "Section": "post",
  "comments": true
}

Recent developments in [MindsEye](https://github.com/SimiaCryptus/MindsEye) have yielded greatly increased speed and scalability of network training. Major improvements to the OpenCL kernels have increased speed in some tests by 50x or more, and data-parallel training has been tested with a Spark cluster. This combination of GPU and cluster computing support should bring MindsEye much closer to the performance and scale of other frameworks, if not in the competitive range! The componentization of the optimization code that I wrote about previously has enabled [Spark support](https://github.com/acharneski/ImageLabs/blob/master/src/main/scala/interactive/SparkTrainable.scala) to be implemented in only about 100 lines in one self-contained class, a nice result of careful design.

Cluster computing is going to be a very necessary feature for modern NN frameworks, because several factors are increasing:

1. Modern networks are much larger in both depth and width
1. Some new components, such as convolutional layers, involve increasing amounts of CPU in comparison to the number of weights. This trend goes along with the trend towards deeper networks via the intuition that the weights will “contain” more “knowledge” in these configurations.
1. Data availability is increasing exponentially, as are the size of datasets generally used in training sessions.

To illustrate, let’s look at one convolutional layer you would find in a network similar to [GoogLeNet](http://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Szegedy_Going_Deeper_With_2015_CVPR_paper.pdf). It applies a 5x5 convolution, transforming the 3-band input RGB image into a 2-band image with the same resolution, and it is used on a 256x256 input image. It has 5x5x3x2x256x256 = 10 million operations per image, with only 150 weights. So, for every iteration of training, which involves 100 images randomly sampled, we are talking 1 billion “operations”, each of which of course actually involve many actual CPU instructions. Now consider that this layer is just one sub-component of a larger “Inception” layer, each of which consists of between 4-7 convolution layers. There are 9 Inception layers plus a few other components in GoogLeNet. And, of course, there are many iterations of training... perhaps 1e3 to 1e5 until any useful convergence. A typical figure quoted for training GoogLeNet is around a week on a single, high-end single-GPU desktop. Obviously, the results of these training sessions are quite valuable, as is the computing resources used to generate them.

__A rough estimate of GoogLeNet’s training time if hosted on AWS would give a cost of around $100, for 5 million parameters in the model or about $1 per 50kB. With around 10e15 synapses in the human brain, we arrive at a rough estimate for the value of a life: $200 billion. Fun Stuff!__

Then of course is the matter of getting un/lucky and converging far faster or slower than statistically expected... This makes me wonder how intellectual property might be enforced when it comes to AI models… in a sense, trained models could be seen as a type of cryptocurrency, or perhaps a cryptocommodity.

One “ah-ha” moment I had the other day was upon realizing the importance of what I might call the “image tensor schema”: First, we realize that we have two spacial dimensions, and elements along these dimensions are in a regular pattern we can use to define shared weights - the weight between (1,1) → (2,2) is the same as the weight between (2,3) → (3,4). This is an important but well covered concept, so far so good. Now we have two more dimensions: “color” bands and batch index.

“Color” is in quotes because signals in the middle of a neural network generally do not represent color, but nonetheless they are the orthogonal dimension that allows each pixel to have a multidimensional value. This band dimension is “fully connected” - if you have two output channels A and B, and three input channels R, G, and B, then each of the 6 distinct connections will have individual weights. “Fully connected” differs from a “convolutional” dimensions because convolutional weights are generally 0 outside a small rectangular neighborhood and thus not “connected”.

The final dimension isn’t one you usually think about, but it is a necessity of implementation and its existence does become important in certain other types of layers; this is the dimension of the array that organizes your batch of training samples - the “batch” dimension. This dimension is “Non-connected” in that each separate batch is isolated - different batches are not connected at all. Considered together, these four dimensions have a certain pleasing symmetry of function, which is evident in the three OpenCL kernels: [convolve](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/opencl/ConvolveKernel.java), [backprop](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/opencl/BackpropKernel.java), and [learn](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/opencl/GradientKernel.java).

Understanding the above is important when constructing a convolutional weight layer, since when you construct it you need to supply the kernel size. The kernel is the set of weights, and for the first two spatial dimensions they are easy to understand - a 5x5 kernel has 25 weights distributed around a rectangular neighborhood with width and height 5. The third dimension, however, is where you need to specify the number of weights. This is the number of input bands (e.g. 3 for RGB) multiplied by the number of output bands. Thus it is an error if the kernel does not have a multiple of the input’s number of bands. Another important point about convolutional layers is that it is very easy for them to learn an identity function - this may seem almost contrary to being useful, but it actually makes deeper networks possible. Think of it this way - in order for information to propitiate directly from the input to some deeply hidden layer, each layer on top of it will need to involve an identity mapping component. Thus easily-formed identity mappings can serve as virtual connections from the input to deeper network layers.

Overall, the kernel size gives you an effective parameterization with which to process image data, but keep in mind it never changes the width and height dimensions. Also, because of the need for 1-1 pixel centering, kernel width/height must be odd, and connections which spill over the edge are treated as 0.

Next comes the previously mentioned “[Inception](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/graph/InceptionLayer.java)” layer that was introduced by the GoogLeNet paper. This is, in its general form, a set of parallel pipelines which process an input image using a set series of kernels in each pipeline. At the end of each pipeline is then several image tensors, all with the same spatial dimensions but an arbitrary number of bands. A single output image tensor is then formed by [concatenating](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/net/reducers/ImgConcatLayer.java) all the bands together. This is generally followed by a sub-sampling layer to reduce the spatial complexity as appropriate. A sequence of these Inception layers thus progressively “squeezes” the information from the spacial dimensions into the fully connected “color” bands, which become the categorization dimensions.

So finally, in the general architectural pattern of GoogLeNet, we have a pipeline of Inception layers, each of which involves a set of parallel pipelines made of convolution layers. The basic architecture could thus be described using an irregular 6-dimensional integer array, including a number of constraints of course.

My next major goal with MindsEye is to reproduce the training of GoogLeNet using the same architecture against the same dataset (ImageNet 2014). Currently, I am working on the kinks of getting OpenCL working on AWS EMR. Hopefully soon I will follow up with a step-by-step guide on how to build GoogLeNet yourself!

