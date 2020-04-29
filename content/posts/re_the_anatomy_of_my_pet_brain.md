{
  "disqus_url": "http://blog.simiacryptus.com/blog/re_the_anatomy_of_my_pet_brain/",
  "disqus_title": "RE: The anatomy of my pet brain",
  "Title": "RE: The anatomy of my pet brain",
  "Pubdate": "2015-10-18",
  "Keywords": [
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "re_the_anatomy_of_my_pet_brain",
  "Section": "post",
  "thumbnail": "/img/c2550ef7-e2fb-4d7f-b54d-82d97e3c1fb2.png",
  "comments": true
}

In my last post, I talked about a new project I was working on to explore convolutional neural networks (CNNs). I've spent much of the time since playing with and iterating on this library, and I wanted to take a moment to share what has been built so far. I've ended up with a library of 30 network layer types which can be wired in an arbitrary directed acyclic (non-recurrent) graph/network and perform gradient descent training and optimization. Numerical performance on my machine is around 10-250 million connection updates per second (MCUPS) depending on the network. A variety of tests provide over 80% code coverage. It can, for example, produce a learned model to classify the MNIST dataset with 90%+ accuracy in a couple minutes. It weighs in at just under 5000 lines of (non-test) code with minimal required dependencies. For high-performance computations, it has an optional dependency on Aparapi and JBLAS.

# Background

Links for theory and prior art – I am far from the first to write about this topic, so I won't bother reviewing the background beyond providing a few links I found to be most useful:

1. https://web.stanford.edu/class/cs294a/sparseAutoencoder.pdf – Although it talks specifically about sparse autoencoders, it covers most functional areas of this library
1. http://deeplearning.stanford.edu/wiki/index.php/UFLDL_Tutorial – Useful wiki, related to the above link.
1. http://deeplearning4j.org/ - scala/java library for neural networks
1. http://www.heatonresearch.com/encog/ - java implementation of neural networks
1. http://googleresearch.blogspot.com/ - A constant source of interesting and relevant (usually) articles
1. http://jmlr.csail.mit.edu/proceedings/papers/v9/glorot10a.html – Good, highly cited research paper.

## Key Problems and Lessons Learned
1. Follow test driven development practices, especially with regard to checking component gradients with finite difference estimation
1. Don't bother writing a naive component implementation (e.g. gradient formulation) if it scales badly. My first draft of e.g. the softmax layer had an O(n^2) complexity since I was computing the full gradient matrix, requiring an almost immediate rewrite.
1. Use a specific set of realistic tasks for performance tuning and considerations – They vary greatly in scaling parameters!
1. Keep the bulk of the processing consolidated into a small number of tightly nested loops. This results in simpler code and faster execution. I saw a significant increase in performance when I implemented batch calculations; I really only did this so I could implement a sparsity meta layer, but it was a large and welcome side-effect. 0.25 million function call boundaries each second can add up! 
1. Similar to #4, consolidating multidimensional rectangular arrays into a single schema-aware class backed by a single array can make a big difference in performance by easing load on the memory management system.
1. Design for cross-cutting concerns (such as diagnostic logging) before polluting your component library with low-value code. An aspect oriented programming model for these components could be a great feature for a library like this. I have addressed some of these use cases via encapsulation and “utility” layer types.
1. Keep the learning algorithm pure – implement the specifics of a network purely in the differentiable gradient descent component network. Things like sparsity constraints, regularization, etc can be implemented as adjustments to the fitness function being optimized in preference to adjustments to the learning procedure. This library is currently sufficient with a basic adaptive-rate gradient-descent loop.
1. Less is more – I have removed a lot of experimental code from this project. Not because all the experiments failed, they just don't belong as a part of the core release. Removing the nonessential leaves us with a common basis of code that can be easily understood and used for a variety of experiments.
1. How you implement the wiring together of components to form a network is very important to think about. Is it a simple sequence? A directed acyclic graph? Recurrent? How should the user code look? Consider the capabilities of this structure versus its complexity, and consider how the language api will look when it is used to build nontrivial networks. This interface is the primary component of the “feel” of the overall library.
1. Another key problem is tracking the metadata/schema describing the format of number arrays used as inputs/outputs. Ideally these constraints could all be enforced by the type system. They should be enforced as early as possible, since mismatches can lead to strange and rarely useful behaviors which can be hard to diagnose. Examples of this metadata include: 
    1. multidimensional array dimensions for convolutional processing
    1. expected bounds for values; e.g. entropy loss layers give non-finite results for negative inputs
    1. normalization: An easy way to get positive results from an entropic loss layer is to input all 1's and ignore the requirement the input values sum to 1.

## Architecture
I will survey – quickly – the overall architecture and components of this library to give a feel of the of the scope, both in breadth and volume. I've tried to keep this library to the essentials, but even still this overview feels pretty verbose. This was one surprising thing to me about this project – how many parts there are in the minimal viable product.

# Basic Utility Classes 
First, there are some core data structures and interfaces we will use throughout the project:

1. NNLayer – Defines the basic contract for a neural network component. Fundamentally, it has to be capable of computing a function and its gradient. The ability to encapsulate and combine these layers is also important, as is performance, so these are all considerations for this contract.
1. NNResult – This class encapsulates a (feed-forward) result along with an implementation method to compute the gradient on demand, i.e. trigger backpropagation
1. NDArray – Encapsulates a single array of doubles along with multidimensional schema information so it can be treated efficiently as an N-dimensional rectangular array.
1. Misc utility methods and data classes – Nothing too special

## Testing Infrastructure 
The machine learning space is a great example of the importance of Test Driven Development. Since you are building a machine out of components which are designed to adapt to whatever context to achieve a target result, you can easily have one severely broken component in the middle of your AI program which is so compensated for by other components that the overall system is broken in a minor and often hard to debug way! Thus it is important to test each component and composite in isolation and verify the expected behaviors as closely as possible.

1. Gradient Checking Unit Tests – The first class of tests for neural network components evaluates prototype inputs and uses finite difference methods to verify the results of gradient evaluations. Do not develop or use components without at least this level of verification! These can also be extended to perform scaling and performance tests.
1. Simple Network Tests – Once components are verified, one needs to test them at a slightly more complex level where they learn trivial problems. Often this takes the form of a single bias layer allowing the inputs to be converged to an expected output. A library of very simple network layouts and very simple test problems is provided for regression testing.
1. Misc unit tests – A variety of unit tests are also needed for more specific components, such as unit tests for the Aparapi / OpenCL kernels.
1. High level tests – More complex networks and training problems are packaged as junit tests in this project – I find it to be a convenient execution harness. Results are discussed in the last section.

## ComponentLibrary 
The component library is the meat of this project and I will only give a very brief survey. Architecturally, it is important that the components support the NNLayer contract and does not leak other implementation details to other components.

1. Activation Layers – Sigmoid, Softmax, etc – Classical, stateless differentiable functions used to introduce nonlinear effects in neural networks. For layers like softmax that are not simple univariate functions, it is important to avoid nested loops and N^2 computational complexity.
1. Basic – Bias, Synapse Layers – Your basic state classes, performing vector addition and matrix multiplication.
1. Development – JBLAS/OpenCL synapse layers – Although this package is for any non-canonical, experimental, or in-development components, it currently houses 2 alternate implementations of the DenseSynapseLayer (a fully connected weight matrix). The JBLAS implementation seems to be the winner.
1. Loss Functions – RMS and Entropy – These layers compare euclidean or probabilistic results with expected values and produce a differentiable error function that can then be optimized to achive supervised learning.
1. Media – Convolutional Neural Networks – These components, such as the ConvolutionalSynapseLayer and MaxPoolingLayer, are designed to work on 2d image data in ways that are position-independent and/or neighborhood-local.
1. Meta – These components enforce constraints on global behavior of the network across training samples. This differs greatly from other components that are designed to work identically whether they process the dataset one-at-a-time or in batch. A good example of this type of component is the sparsity constraint component.
1. Reducers – Avg, Sum, Max, etc – Like activation layers, these are simple stateless functions, but they usually serve more of a structural than a functional purpose.
1. Utils – A variety of useful methods that are more programmatic than mathematical in nature.
    1. Verbose Logging – This component wraps a layer to provide verbose logging. Similar wrappers would be a good way to gather other diagnostics and similar cross-cutting concerns.
    1. Weight Extraction – Many of these components are stateful and contain weight vectors that we may want to normalize via an adjustment to our fitness function. This component allows the state of a component to be exposed directly to the network.
    1. Wrapper Layer – This provides a stub wrapper so that the inner implementation can be replaced as desired. This is useful when developing networks whose layout changes over time.


## DAGNetwork
 
This class encapsulates many neural components to form a single directed acyclic graph which can be treated as a single neural component. It is the main structural class for this library.

It builds a sequence of nodes, each of which tie one component to other nodes. During each evaluation, the nodes act as lazy evaluators to evaluate the required network outputs.

A simple network layout looks something like:

```java
DAGNetwork net = new DAGNetwork()
    .add(new DenseSynapseLayer(NDArray.dim(inputSize), midSize))
    .add(new BiasLayer(midSize))
    .add(new SigmoidActivationLayer())
    .add(new DenseSynapseLayer(NDArray.dim(midSize), outSize))
    .add(new BiasLayer(outSize))
    .add(new SigmoidActivationLayer());
net.addLossComponent(new SqLossLayer());
```

Whereas more complex layouts are also possible:

```java
this.net = new DAGNetwork();
List<> weightNormalizationList = new ArrayList<>();
DenseSynapseLayerJBLAS encode = new DenseSynapseLayerJBLAS(NDArray.dim(outerSize), innerSize);// .setWeights(()->Util.R.get().nextGaussian()*0.1);
weightNormalizationList.add(encode);
{
    net = net.add(encode);
    BiasLayer bias = new BiasLayer(encode.outputDims);
    weightNormalizationList.add(bias);
    net = net.add(bias);
    net = net.add(new SigmoidActivationLayer().setBalanced(false));
}
center = net.getHead();
{
    DenseSynapseLayerJBLAS decode = new DenseSynapseLayerJBLAS(NDArray.dim(innerSize), outerSize)
    .setWeights((Coordinate c) -> {
    int[] traw = new int[] { c.coords[1], c.coords[0] };
    int tindex = encode.getWeights().index(traw);
    Coordinate transposed = new Coordinate(tindex, traw);
    double foo = encode.getWeights().get(transposed);
    return foo;
    });
    weightNormalizationList.add(decode);
    net = net.add(decode);
    BiasLayer bias = new BiasLayer(decode.outputDims);
    weightNormalizationList.add(bias);
    net = net.add(bias);
    // net = net.add(new SigmoidActivationLayer());
    feedback = net.getHead();
}
List fitnessSet = new ArrayList<>();
fitnessSet.add(this.net
    .add(new SqLossLayer(), this.feedback, this.net.getInput().get(0))
    .add(new AvgMetaLayer()).getHead());
fitnessSet.add(this.net.add(new Sparse01MetaLayer(), this.center)
    .add(new SumReducerLayer())
    .add(new LinearActivationLayer().setWeight(.1).freeze()).getHead());
fitnessSet.add(this.net.add(new SumInputsLayer(), weightNormalizationList.stream().map(x->net
    .add(new WeightExtractor(0, x), new DAGNode[] {})
    .add(new SqActivationLayer())
    .add(new SumReducerLayer()).getHead()).toArray(i->new DAGNode[i]))
    .add(new LinearActivationLayer().setWeight(0.001).freeze())
    .getHead());
this.net.add(new VerboseWrapper("sums", new SumInputsLayer()), fitnessSet.toArray(new DAGNode[] {}));
```

# Trainer Methods
Although I have played with an experimented on variations of the learning algorithms, my first published version is sufficient with a first-order gradient descent procedure with a simple adaptive rate. Alternate methods such as L-BFGS and PSO are planned for the future. Outside these methods (implemented and not), there are a variety of methods to select training sets to optimize learning, putting the “stochastic” in stochastic gradient descent. This method is used, implicitly, by several test examples.

# Results
Classification Regions
To help visualize and explore the behavior of these systems at low dimensions, I've created a suite of test categorization problems. This uses a randomly set of population points in 2d space drawn from a variety of patterns. Some patterns are easy for a simple network to classify, and others are nearly impossible (for simple networks):

```
ClassificationResultMetrics [error=0.13045791649812016, accuracy=1.0, classificationMatrix=[ [ 100.0,0.0 ],[ 0.0,100.0 ] ]] 
TrainingContext [evaluations=Counter [value=698.0], calibrations=Counter [value=0.0], overallTimer=Timer [value=0.0], mutations=Counter [value=0.0], gradientSteps=Counter [value=162.0], terminalErr=0.01]ClassificationResultMetrics [error=0.18390882304814632, accuracy=1.0, classificationMatrix=[ [ 100.0,0.0 ],[ 0.0,100.0 ] ]] 
TrainingContext [evaluations=Counter [value=100558.0], calibrations=Counter [value=0.0], overallTimer=Timer [value=0.0], mutations=Counter [value=0.0], gradientSteps=Counter [value=23206.0], terminalErr=0.01]ClassificationResultMetrics [error=1.0292766269432674, accuracy=0.995, classificationMatrix=[ [ 100.0,0.0 ],[ 1.0,99.0 ] ]] 
TrainingContext [evaluations=Counter [value=102551.0], calibrations=Counter [value=0.0], overallTimer=Timer [value=0.0], mutations=Counter [value=0.0], gradientSteps=Counter [value=23665.0], terminalErr=0.01]ClassificationResultMetrics [error=6.799908397558712, accuracy=0.615, classificationMatrix=[ [ 61.0,39.0 ],[ 38.0,62.0 ] ]] 
TrainingContext [evaluations=Counter [value=17300.0], calibrations=Counter [value=0.0], overallTimer=Timer [value=0.0], mutations=Counter [value=0.0], gradientSteps=Counter [value=3984.0], terminalErr=0.01]ClassificationResultMetrics [error=0.30472166219228297, accuracy=1.0, classificationMatrix=[ [ 100.0,0.0 ],[ 0.0,100.0 ] ]] 
TrainingContext [evaluations=Counter [value=539.0], calibrations=Counter [value=0.0], overallTimer=Timer [value=0.0], mutations=Counter [value=0.0], gradientSteps=Counter [value=125.0], terminalErr=0.01]ClassificationResultMetrics [error=0.12145764920083349, accuracy=1.0, classificationMatrix=[ [ 100.0,0.0 ],[ 0.0,100.0 ] ]] 
TrainingContext [evaluations=Counter [value=201.0], calibrations=Counter [value=0.0], overallTimer=Timer [value=0.0], mutations=Counter [value=0.0], gradientSteps=Counter [value=47.0], terminalErr=0.01]ClassificationResultMetrics [error=0.5919904265308571, accuracy=1.0, classificationMatrix=[ [ 100.0,0.0 ],[ 0.0,100.0 ] ]] 
TrainingContext [evaluations=Counter [value=20709.0], calibrations=Counter [value=0.0], overallTimer=Timer [value=0.0], mutations=Counter [value=0.0], gradientSteps=Counter [value=4779.0], terminalErr=0.01]ClassificationResultMetrics [error=0.13615430754693006, accuracy=1.0, classificationMatrix=[ [ 100.0,0.0 ],[ 0.0,100.0 ] ]] 
TrainingContext [evaluations=Counter [value=22.0], calibrations=Counter [value=0.0], overallTimer=Timer [value=0.0], mutations=Counter [value=0.0], gradientSteps=Counter [value=6.0], terminalErr=0.01] 
```



# MNIST Classification
Since my main target for this project has been 2d image processing, the MNIST dataset is a prominent test problem. One basic step is to carry out simple supervised classification of the digits, which our network demonstrates with about a 90% success rate, which is standard for a simple logistic regression. It can train against the unsampled training set at about 250MCUPS and achieves 90% in about 2 minutes.

Here is the categorization matrix plot that is output at the end:

## MNIST Sparse Autoregression
Another experiment is my reproduction of the sparse autoencoder detailed on the standford deeplearning wiki. The network specification is the example above for a “more complex” DAGNetwork layout. The test will output a report with example images resulting from the full-feed-forward evaluation of the network (i.e. the feed-forward reconstruction) after each macro-iteration of training. Here is an example sequence a few minutes into a test run:

```
TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST TEST
```

# Aparapi, OpenCL, JBLAS, and numerical performance
It was surprising to me that something as simple as matrix multiplication could have such nuanced performance considerations. You'd usually think of it as an O(n^2) operation, end of story. But after leveraging cpu instructions, cpu/memory cache levels, specialized hardware and native libraries, you end up getting an operation that is order(s) of magnitude faster, even if it scales the same way!

Comparing the results quantitatively is beyond the scope of this article, but I have experimented with several variations of the matrix multiplication “synapse” layer:

1. Simple, tight java loop – Performed actually pretty well, only about half as fast as JBLAS
1. JBLAS – Performed the best, uses native code.
1. Aparapi – Tested a fairly naïve kernel for matrix multiplication – Was about 50% slower than pure java, but I strongly suspect this can be improved.
(All computations are done using doubles.)

# Deconvolution
Another interesting use case for this library is image reconstruction from lossy operations such as linear motion blur. I detailed some results in this area in my previous post.

# Plans for the future
I wrote this library because I wish to experiment with these methods and compare my results with others', hopefully improving the state of the art. This post just details my experience progressing towards that end. Research ideas I have to follow up with this include:

Alternate training methods – Many other methods – both documented in literature and floating in my head – could be used to optimize the parameters of the system.
Additional components – I am particularly interested in structures that unify concepts such as GMM, PCA, Kernel/RBF, tree/forest, and ensemble models with neural networks.
Aparapi optimizations and more exploration of CNNs – A large inspiration for this project has been Google's recent publications on neural network image recognition and reconstruction - I would like to continue following that line of research.
Integration with Spark – The ability to train against larger data sets using a cluster of machines could open up interesting new lines of research, or at least could be worth writing about.
Rewrite in scala - Many scala language features such as operator overloading, traits, and implicits could make this library much... better...er.
Numerical/Signal Basis Transforms - Convolutional networks can be efficient to train in the fourier domain. Likewise, there can be advantages to expressing neural signals using integers or in a logarithmic basis. (Generally the advantages of such exotic approaches are gains in computational efficiency.)

More soon, I hope!