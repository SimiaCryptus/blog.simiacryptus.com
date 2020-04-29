{
  "disqus_url": "http://blog.simiacryptus.com/blog/test_driven_development_for_neural_networks_part_ii__ab_testing/",
  "disqus_title": "Test Driven Development for Neural Networks, Part II - AB Testing",
  "Title": "Test Driven Development for Neural Networks, Part II - AB Testing",
  "Pubdate": "2017-12-13",
  "Keywords": [
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "test_driven_development_for_neural_networks_part_ii__ab_testing",
  "Section": "post",
  "thumbnail": "/img/5e804747-77dd-4c2b-b63f-74368594c2cc.png",
  "comments": true
}

In the last article, we covered a common testing framework for individual components, but we didn’t cover how these networks are actually trained. More specifically, how should we design a test suite to cover something so broad as optimization? A big problem here is that the components are heavily dependent on each other and also vary greatly in function and contract, and so there are few opportunities for generic testing and validation logic. One simple way to test these on functional level is to use them on demonstration problems, perhaps with the notebook format we used for our component unit tests. This prevents us from isolating every component, and opens up a myriad of possible ways we could configure tests, but it’s a start.

The basic version of this method is to establish a baseline demonstration notebook. In MindsEye I have used the [MNIST handwritten digit classification problem](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/opt/MnistTestBase.java) to be the baseline; it’s pretty much the [“Hello World” of AI](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/reports/com/simiacryptus/mindseye/opt/trainable/SimpleStochasticGradientDescentTest/test.md). We start with this problem being solved in the most basic way using the most basic network and the simplest functional optimization setup. For each component, we derive a test from this template and override appropriate methods to plug in our component; this provides the flexibility to demonstrate the component’s properties, such as sparsity.

Inheritance alone, though flexible, provides limited ability to capture the complex combinatoric nature of optimization setups. To improve this and allow better coverage of the possibilities, I’ve designed a framework to assist with this combinatoric test problem. This framework allows you to establish various interchangeable strategies, so that once setup they can combine interchangeably to produce new tests. For an executable test, you must simply select one strategy each of the following types:

1. Network - how is it setup? Examples:
    1. [Simple single-layer linear](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/labs/matrix/MnistTests.java#L46)
    1. [Simple convolutional network](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/labs/matrix/MnistTests.java#L60)
    1. Deep convolutional network
1. Optimization configuration - involves the choice of several sub-strategies and metaparameters. Examples:
    1. [Stochastic Gradient Descent](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/labs/matrix/TextbookOptimizers.java#L56)
    1. [Conjugate Gradient Descent](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/labs/matrix/TextbookOptimizers.java#L72)
    1. [L-BFGS](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/labs/matrix/TextbookOptimizers.java#L87)
    1. [OWL-QN](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/labs/matrix/TextbookOptimizers.java#L103)
1. What dataset are we studying?
    1. [MNIST](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/labs/matrix/MnistTests.java) - A small gray scale image tile classification data set which is easy to achieve ~91% on. Gray scale 28x28 images for each 0-9 digit.
    1. [CIFAR](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/test/java/com/simiacryptus/mindseye/labs/matrix/CifarTests.java) - Another, much more difficult small image tile classification data set. Color 32x32 images in 10 categories.
1. Method - This defines various ways that a network is used. Examples:
    1. [Classification](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/main/java/com/simiacryptus/mindseye/test/ClassifyProblem.java) - Learn to classify the images
    1. [Representation](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/src/main/java/com/simiacryptus/mindseye/test/EncodingProblem.java) - Derive a common decoding network and input values which reconstruct the data set
    1. Denoising Autoencoder

Just in the 12 example strategies listed above, we could easily define 72 separate tests. Adding a single new strategy will increase that number by 18-36 possible tests; the point being the effort required to create new tests is so low that the main effort is now judiciously choosing which ones to actually execute. The standard reports published with MindsEye can be found in the [reports directory](https://github.com/SimiaCryptus/MindsEye/tree/3053e759f8cf0921157fe24df80f4a1e90069c00/reports/com/simiacryptus/mindseye), mostly in [labs/matrix](https://github.com/SimiaCryptus/MindsEye/tree/3053e759f8cf0921157fe24df80f4a1e90069c00/reports/com/simiacryptus/mindseye/labs/matrix).

So now we can run all our code with test cases, in a variety of setups, each producing a detailed report, with minimal effort. In addition to testing, documentation, and demonstration, this is an ideal platform to support an AB testing process. By looking at the results for a variety of problems solved identically except for one given change, we can determine how effective various options are in various situations. For example, this [test report](https://github.com/SimiaCryptus/MindsEye/blob/3053e759f8cf0921157fe24df80f4a1e90069c00/reports/com/simiacryptus/mindseye/labs/matrix/OptimizerComparison/CompareTextbook/classification.md) compares various optimization methods on a particular problem, resulting in the following graph:

![](/img/5e804747-77dd-4c2b-b63f-74368594c2cc.png)

This completes our review of the testing strategy for MindsEye. Using this highly-leveraged framework, we can ensure that every component, and any new ones, are well tested with accurate documentation.
