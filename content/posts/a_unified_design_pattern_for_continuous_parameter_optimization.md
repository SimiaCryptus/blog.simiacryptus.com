{
  "disqus_url": "http://blog.simiacryptus.com/blog/a_unified_design_pattern_for_continuous_parameter_optimization/",
  "disqus_title": "A Unified Design Pattern for Continuous Parameter Optimization",
  "Title": "A Unified Design Pattern for Continuous Parameter Optimization",
  "Pubdate": "2017-05-09",
  "Keywords": [
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "a_unified_design_pattern_for_continuous_parameter_optimization",
  "Section": "post",
  "comments": true
}

Almost two years ago I developed a neural network library called [MindsEye](https://github.com/SimiaCryptus/MindsEye), which has largely sat idle since the release of TensorFlow. Recently however I’ve wanted to follow up on research involving neural networks, but I wanted a “pure” java option I could use for research. And so I decided it was time to revive my old project.

In this release, I have reviewed all of the code and made many improvements. The optimization code has been rewritten (more on that below), and I have added the L-BFGS and OWL-QN learning algorithms. The OpenCL binding has been updated to a version that is managed as a Maven artifact, with automatic native library loading. A new component similar to convolution has been added which supports generic Toeplitz matrices/tensors and is faster for small images.

One major goal in designing MindsEye was to provide a very customizable optimization framework. I hope to provide a unified pattern under which many popular algorithms can share common functionality. It is my hope that this enables research into alternative, hybrid, and novel methods. For standard use several textbook methods are included, such as SGD, L-BFGS, and OWL-QN.

The pattern is explained below and implemented in Java in the [MindsEye opt package](https://github.com/SimiaCryptus/MindsEye/tree/master/src/main/java/com/simiacryptus/mindseye/opt). It consists of several interfaces that are designed to be understandable and customizable. At the highest level, it has 4 functional layers, one of which encapsulates the last two:

1. Prepare the function to optimize
1. Search strategy
1. Direction Finding
1. Line Search 

These are described in more detail below.

Multivariate optimization requires a function to optimize, and we get this function by combining our network with a training data set and a loss function. The loss function is combined with our subject network in a special supervised training network that has only a single output. (Provided loss functions include root-mean-squared and entropy.) This network can then be evaluated against a training data set, and the results (including gradients) summed up to produce a differentiable function that depends only the network weights. How this evaluation happens, and what exact data set is used, can be varied by implementation. For example, this component could implement stochastic data sampling or execution over a spark cluster (data-parallel). This optimization problem, once prepared, can be wrapped to provide L1 and L2 normalization.

Once we have our function, which is a self-contained optimization problem that hides virtually all details of the network or data set, we can give it to a generic optimizer. The four components of the Optimizer are the Iterator, the Orienter, the Stepper, and the Monitor.

The Iterator will define the api for using the optimization process, and is where an asynchronous or interactive api might be defined, for example. The reference [IterativeTrainer](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/opt/IterativeTrainer.java) implementation will synchronously search in a loop, using a single starting point defined by the state of the given network, and modifying the weights of that network in-place. This layer is another place cluster-parallelism such as Spark could be leveraged, such as when using multiple search points as in a particle swarm.

The Iterator will call the Orienter and Stepper in a loop, passing the Monitor object around to provide debugging callbacks. The Orienter will determine the direction a given step should take, and the Stepper both determines the size of the step and performs the step, updating the model. This process probably sounds familiar.

The Orienter is a strategy to determine the search direction. The simplest example for a differentiable function is “steepest descent” which blindly modifies the weights in the direction of the gradient.

In the case of the [L-BFGS](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/opt/LBFGS.java) algorithm, it uses previously sampled points (along with their gradients) to estimate something known as the inverse Hessian. The Hessian is to a gradient as a second derivative is to a first, and knowing it can allow us to adapt our step since instead of a linear local model we now have a quadratic local model, which has a known minimum. This makes a more informed selection of both our step direction and our step size (since the orientated step is not necessarily a unit vector).

In the case of [OWL-QN](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/opt/OwlQn.java), the Orientation strategy passes a “line search problem” to the stepper that isn’t a simple linear relation. Instead, the line is constrained to the current “orthant”, and will follow the orthant boundaries where some weight values are zero. This “trust region” approach is very effective in finding a sparse model where many weights are zero.

The Stepper searches along the given univariate function, also known as a “line search”. On each step, it measures the fitness and derivative, and will iteratively attempt to find an approximate (or exact) minimum along that line. Our [default implementation](https://github.com/SimiaCryptus/MindsEye/blob/master/src/main/java/com/simiacryptus/mindseye/opt/ArmijoWolfeConditions.java) uses an adaptive step size window that is determined by what are known as the Armijo and Wolfe line search constraints, and takes a single “acceptable” step. These constraints basically ensure that the step size is not to large or small, respectively, by comparing both the value and gradient over the step.

Finally, the Monitor provides a way for the executing application to monitor the progress of the task, capturing logging and taking snapshots, for example. It may also determine auxiliary stopping conditions.

This pattern should be well suited for many algorithms and related use cases, such as:

* Simple Gradient Descent (provided)
* Stochastic Gradient Descent (provided)
* Conjugate Gradient (left as an exercise for the reader!)
* L-BFGS (provided)
* OWL-QN (provided)
* Particle Swarm Optimization
* Data- and Cluster- parallel execution
* Hybrids and variations of above - This library is intended to be research-friendly
* And more!

I am currently working on a [number of notebooks](https://github.com/acharneski/ImageLabs/tree/master/reports) that demonstrate textbook problems and solutions, such as MNIST classification and autoencoders. Eventually I hope to provide AI-powered image processing solutions using this library, and to combine it with [reSTM](https://github.com/SimiaCryptus/reSTM) to provide an online AI service.

Overall, this new release brings the MindsEye library a long way towards being a competitive neural network / deep learning library. I think it is now to a point where it is a viable alternative to mainstream libraries, with the advantage of being Java based, lightweight, and highly customizable. Enjoy!
