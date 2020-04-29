{
  "disqus_url": "http://blog.simiacryptus.com/blog/test_driven_development_for_neural_networks_part_i__unit_testing/",
  "disqus_title": "Test Driven Development for Neural Networks, Part I - Unit Testing",
  "Title": "Test Driven Development for Neural Networks, Part I - Unit Testing",
  "Pubdate": "2017-12-04",
  "Keywords": [
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "test_driven_development_for_neural_networks_part_i__unit_testing",
  "Section": "post",
  "comments": true
}

A critical part of any good software is test code. It is an understatement that tests improve quality; they improve the scalability of the entire software development process. Tests let you write more code, faster code, better code. One of the leading testing methodologies is unit testing: the philosophy of breaking down software into individual components and testing each separately. It turns out that a great case study in unit test design also happens to be one of today’s hot tech topics - artificial neural networks.

Known by a plethora of names and acronyms, neural networks are a modular data processing structure whose form is inspired by biological neural networks. A core learning algorithm/property used is back-propagation; it enables the iterative improvement (known as Gradient Descent) of the myriad of free variables within an arbitrarily complex network to improve a scalar “fitness” output - a process also known as machine learning.

Therefore, key components in developing neural software include:

* A [library](https://github.com/SimiaCryptus/MindsEye/tree/master/src/main/java/com/simiacryptus/mindseye/layers) of components
* A [way](https://github.com/SimiaCryptus/MindsEye/tree/master/src/main/java/com/simiacryptus/mindseye/network) to wire them together
* A [way](https://github.com/SimiaCryptus/MindsEye/tree/master/src/main/java/com/simiacryptus/mindseye/opt) to train them

Today, we’ll be talking about #1.

# Testing Requirements

Back-propagation uses the chain rule to ensures [composability](https://en.wikipedia.org/wiki/Composability), which allows the construction of arbitrarily complex networks. This means each component must provide executable implementations of both a multivariate function and its derivative. Although in practice this function should be fairly smooth, in principle the function is arbitrary and can even have kinks. The big requirement, however, is that the derivative agrees with the functional. We’ll call this “numerical consistency”.

It turns out that this component library can grow fairly large. Just in my personal research, I have 70 layers in the current version of MindsEye. With a library that large, I have not only found it challenging to maintain quality, I have even had a hard time remembering what a layer is supposed to be doing! I try to make the names self-explanatory, but it is clear that we need documentation in addition to quality assurance.

There are good reasons that, at the time of this writing, the Universal AI hasn’t taken over the world. One big reason is it isn’t fast enough yet - speed has therefore often determined the rate of development. It follows that we are interested in performance benchmarks, and these should be tested and documented.

In order to gain faster performance, especially in the field of GPU-accelerated components, we may use a lower precision such as 32 or even 16 bit floats, or there may be other minor details in how the function is implemented. Usually this will behave fine, but we certainly want to keep an eye on it. When we verify the behavior of this function, we therefore expect some amount of small but acceptable error from what we’d consider the analytically ideal value. This error can be significant in certain cases, and we’d like to document this numerical accuracy.

Another important and often overlooked requirement for a neural network is the ability to save and load it from memory, and communicate it with others. Our documentation should include the serialization format, and the tests should ensure valid serialization.

# Implementation

So in summary, we want to do the following for each component:

1. Documentation
    1. Document what it does
    1. Document the serialization format
1. Testing that the function “behaves”
    1. Ensure it is a numerically consistent function
    1. Ensure it is an accurate function
1. Quantitative benchmarks for incremental improvement
    1. Benchmark the performance 
    1. Benchmark the accuracy

There is a great software pattern that can be used to address the testing and documentation requirements with the same shared code: A notebook. Basically, the idea is for a single-threaded script to output a report that interleaves code with the results of that code’s evaluation. The result is a document produced by a test case, containing a demonstration of most up-to-date implementation of the given component. It can, for example, simply evaluate network.toJson() and document the serialization format. In MindsEye we use a custom notebook library to generate reports in GitHub Markdown.

We would like to design a notebook which tests and demonstrates all key aspects of our component. In order to do that, it is not enough to specify the component - it has to be a specific configuration of the component, with supplied inputs. Therefore our [base class](https://github.com/SimiaCryptus/MindsEye/blob/master/src/test/java/com/simiacryptus/mindseye/layers/LayerTestBase.java) requires only these two definitions, and further testing is defined by additional report configurations.

So how do we demonstrate what a component does? One obvious response is to simply print out some example inputs and outputs - this is the default of our report. If the component is itself a network of sub-components, we could visualize the network using a [graph visualization](https://github.com/SimiaCryptus/MindsEye/blob/f88306790ff34d6c6d04863793e6351f94151a28/reports/com/simiacryptus/mindseye/layers/cudnn/f64/ConvolutionNetworkTest/test.md). If the component is a simple uni-variate [activation function](https://github.com/SimiaCryptus/MindsEye/blob/f88306790ff34d6c6d04863793e6351f94151a28/reports/com/simiacryptus/mindseye/layers/java/GaussianActivationLayerTest/test.md), a plot would be nice. Another way to demonstrate what a component does is by comparison; demonstrate that it does the same thing as another component (i.e. a [reference implementation](https://github.com/SimiaCryptus/MindsEye/blob/f88306790ff34d6c6d04863793e6351f94151a28/reports/com/simiacryptus/mindseye/layers/cudnn/f64/ConvolutionLayerTest/test.md).) This is especially useful in performance-critical components which may have several implementations, such as the convolution layer.

Now that we’ve characterized the layer, we need to test that the function “behaves well”. For the most part, our key tool for this is to numerically estimate derivatives using [finite difference](http://mathworld.wolfram.com/FiniteDifference.html) methods and to compare them with the implemented derivatives. One difficulty of this is that the numerical accuracy effects the ability to evaluate small deviations, another is this estimation is sensitive to function smoothness. However, in most cases it clearly and easily differentiates between a broken and functional implementation. I have developed a fairly thorough [tool](https://github.com/SimiaCryptus/MindsEye/blob/f88306790ff34d6c6d04863793e6351f94151a28/src/test/java/com/simiacryptus/mindseye/layers/DerivativeTester.java) for this.

Another detail that is important to check for, at least in how MindsEye is implemented, is batch invariance. Via programming optimizations, network evaluations are faster when conducted in batch. In training, the network will not generally execute one row of data at a time; it is handled in chunks of some digestible-yet-large batch size. With few exceptions, the components should behave the same whether or not the execution was batched or one-at-a-time.

Finally, we need quantitative figures that indicate a spectrum of continuous improvement to be reflected in our reports. The obvious is performance figures that we’d like to see go to zero or infinity; to gather good performance metrics we simply time how long N executions takes. Another figure, which often describes the performance trade-off penalty, is numerical accuracy.

# Conclusion

In a nutshell, that is how I have ensured quality and scalable development in MindsEye. Due to well defined and testable functionality contracts, a huge library of components can be supported by shared test code requiring only minimal per-component implementation. This is one of the hidden requirements of test code - it is generic enough to 1) be super easy to use, and 2) not go stale.

Thanks for reading, and have an awesome day!

