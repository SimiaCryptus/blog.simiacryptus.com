{
  "disqus_url": "http://blog.simiacryptus.com/blog/deepartistorg_release_10/",
  "disqus_title": "DeepArtist.org Release 1.0",
  "Title": "DeepArtist.org Release 1.0",
  "Pubdate": "2019-09-01",
  "Keywords": [
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "deepartistorg_release_10",
  "Section": "post",
  "thumbnail": "../../img/618be29e-aef5-492a-ba58-3000d8665182.gif",
  "comments": true
}


I'm pleased today to announce the release of the Simiacryptus data tools v1.8.0, including the first version of a new image art publishing application named and located at DeepArtist.org - Notably using the subdomain examples.deepartist.org.

## What is it?

[DeepArtist.org](https://github.com/SimiaCryptus/deepartist.org) is an image processing platform using convolutional neural networks to perform state-of-the-art image processing techniques. This software is targeted at hobbyists and digital artists, and as such this documentation is focused on the practical tools provided to produce pretty pictures. To run locally you need a recent [Nvidia GPU](https://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html#prerequisites-windows), but you can also run these tasks on [Amazon EC2](https://aws.amazon.com/machine-learning/amis/).
In contrast to many contemporary AI projects, this project uses Scala, not Python. I have attempted to simplify things so that very little programming literacy at all is required, and the learning curve is friendly to beginners who want to experiment. One benefit of this approach is that this software runs easily on a variety of systems, including Windows and Mac desktops and on the Cloud.
As you will quickly discover, these painting processes have many controls and settings and can be customized in countless ways. Getting an ideal image result may require quite a bit of experimentation, and you will need a way to track this work. Additionally, you may develop new artistic pipelines, and you may wish to share them. To support these types of workflows, DeepArtist applications output rich text and images as output and have them automatically built into a static website on s3.
A key part of DeepArtist.org are the [examples](http://examples.deepartist.org/) - A set of starting applications that use the platform to demonstrate the basis image processing techniques and concepts.

## How to Install and Run

### Development Tools

First, there are some basic tools needed to run this software:
1. [Java](https://www.oracle.com/java/technologies/javase-jdk8-downloads.html) - You probably have some version of Java, but you will need to install a Java Development Kit so you can compile and run the code. There are several distributions of JDK, many freely available. I use Oracle’s JDK 8.
1. [Git](https://git-scm.com/downloads) - Several friendly distributions and interface wrappers exist for Git, but I prefer the basic command line. You can probably get away without this if you use the IntelliJ git plugin.
1. [IntelliJ](https://www.jetbrains.com/idea/download/#section=windows) - You don’t technically need a fancy development environment, but this is free and well worth this disk space. IntelliJ provides a “community edition” which has basically all the Java features you will need to run this software and develop with it. I used the free version to develop almost all of this software.

### Github

If you aren’t a member of Github, I recommend [signing up](https://github.com/join) for a free account. You can then “fork” examples.deepartist.com so you can have your own copy to customize. You will probably want to [setup the intellij plugin](https://www.jetbrains.com/help/idea/github.html)

### Install CuDNN (sign up with NVidia)

If you want to run jobs locally, and you have a good NVidia GPU, you will need to install CUDNN (CUDA Deep Neural Network Library). If you are not running jobs locally, Amazon Deep Learning instances come with this library pre-installed. Though downloading is free, unfortunately, NVidia has yet to make a public release of this library and requires an NVidia developer membership. Fortunately, this is free to sign up for.
1. [Update GPU drivers](https://www.nvidia.com/Download/index.aspx)
1. [Sign up page](https://developer.nvidia.com/developer-program/signup)
1. [Download page](https://developer.nvidia.com/cudnn)

### Setup AWS, with CLI tools and environment login

AWS is used (optionally) for storing results, serving them as a website, and for executing jobs themselves. An AWS account in itself is free, and you pay for pretty much exactly what you use, but you can still rack up a bill fast if you don’t keep an eye on it. If you want to use it, you will need to sign up for an account, install the command line tools, and establish environment credentials
1. [Sign up for AWS](https://aws.amazon.com/)
1. [Install CLI tools](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
1. [Setup local admin role](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html)
1. [Setup storage bucket and website](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)

### Download and Open Project

Now that the basics are setup, we will download and load the examples project on your system:
1. Clone the [examples.deepartist.org](https://github.com/SimiaCryptus/examples.deepartist.org) repo 
1. Open IDE and Import the project

### Run a local demo - BasicNotebook

We are now ready to run our first project. To simplify things, let’s run a very basic project that doesn’t use any neural networks. Open the examples project and then open the BasicNotebook class.
1. Open class and "run" - Right click the file and choose "run"
1. Load page, confirm configuration - Open a browser to [http://localhost:1080/](http://localhost:1080/). The initial page will prompt the user to edit the settings of the job. You can edit the text to be rendered, the size, the target s3 bucket, and many other settings in other jobs
1. Refresh and upload image - Assuming the content url was left intact, the job will (upon refreshing the page) prompt you to upload an image. Upload one.
1. Wait for completion - One the upload completes, the job runs. This job is fast and will complete in seconds.
1. Examine results - The results will have been saved in a local /reports/ directory that is noted in the output logs, and if setup also on S3.

From here, see and run more involved jobs from [examples.deepart.org](http://examples.deepart.org/).

![](../../img/6b7a20ae-f81f-4e82-9d58-34a6f1953e8d.png)

### Advanced Operation

Things don’t always go as planned, and sometimes you want to do something other than pressing “Run”. This section describes some of these common scenarios

#### Continue aborted optimization

If you have to interrupt a job for any reason, you may want to be able to continue painting where you left off. This is possible by saving the latest image provided via http, and using that image to upload as the initial canvas url.

#### Run on EC2

Any job can be run locally or on EC2. Most jobs are by default coded to run locally, but by modifying or adding a new object which derives from the same class, you can configure the EC2 deployment code. This will use your environment credentials to start a new AWS EC2 instance, upload all the needed code, and remotely start the application. When running, you can manage it via http just as in local execution, and additionally it will send you emails at the start and end of the job run. Watch your execution times! These are Deep Learning instance types, with a high amount of power that comes with a noticeable price tag.
When you run for the first time, you will be prompted to enter your email via stdin, and the role used to start the instance will likely not have all the needed permissions, for example to write to the s3 bucket you intend to publish to. It is recommended that during this first execution, you log into the AWS console and manually assign any needed permissions to the newly created role.

#### Changing port, bucket, and region

Many important settings can be configured via property overrides on the job classes. Of particular note are:
Bucket - Most users will want to configure the bucket field to be something they have access to write to
Http port - If you want to use a port other than 1080, you can override it via the http_port field
Another important config, which is settable via a java property, is the AWS region to use. To use something other than the default us-east-1, simply set the AWS_REGION property e.g. by adding the execution argument -DAWS_REGION=us-west-2

#### Utility HTTP Endpoints

Once an application is running, there are several other pages that can be requested for helpful information:
/cuda/info.txt - This endpoint returns diagnostics text that is returned by the CuDNN library
/shutdown - This endpoint immediately kills the JVM, and if running on EC2 also triggers instance termination.
/threads.json - This endpoint returns information on all stack traces and various thread information from the JVM. Useful for internal code development.
/cuda/stats.json - This endpoint returns profiling data collected during CuDNN invocations. Useful for internal code development.

## Background

This software is built on top of other software and technology.

### Software Technologies:

[CuDNN](https://developer.nvidia.com/cudnn) and CUDA - Nvidia publishes many useful number-crunching libraries that take advantage of the parallel computing abilities of its GPUs. CuDNN in particular is the prefered acceleration library used by deepartist.org. 
[TensorFlow](https://www.tensorflow.org/) - Google’s AI research team has open-sourced Tensorflow, a portable runtime for expressing and running neural networks. This library can be used for importing vision pipelines into DeepArtist.org, such as the pre-packaged Inception model.
Java and [Scala](https://www.scala-lang.org/) - Java is arguably the most popular programming environment today. Scala runs within the Java environment as an alternate language, and is one of the most expressive languages available. Both have a host of free, world-class tools available.

### Image Processing Methods

[Deep Dream](https://ai.googleblog.com/2015/06/inceptionism-going-deeper-into-neural.html) - In 2015 Google Research published Deep Dream, which demonstrated a use of convolutional neural networks to produce interesting visual effects.
[Deep Style Transfer](https://arxiv.org/abs/1508.06576) - In 2016 researchers published a style transfer algorithm using convolutional neural networks, whose approach inspires the bulk of the processing methods used by DeepArtist.org

### Deep Convolutional Networks for Object Recognition

Research into AI requires verifiable research, and to aid that many papers include published pretrained models. These pretrained models can be imported so that the latent patterns they have learned can be used in image processing. At the time of publishing, DeepArtist.org has 3 pre-packaged pipelines which are automatically downloaded upon usage:
[VGG16 and VGG19](https://arxiv.org/abs/1409.1556) - These are large, very simple networks using a series of simple convolution, pooling, and activation layers. As it turns out, the dense and simple structure of these networks seem to provide much better behavior for image processing. 
Inception - A sample import of a tensorflow model, a pretrained inception model is also provided. It uses a more complicated structure to perform well at it’s primary task, classification, with a much smaller size (and a faster speed).

## Examples.deepartist.org
There are a number of examples released with deepartist.org which attempt to illustrate the concepts of these techniques and the capabilities of this software. These examples are free to use as starting points for any of your art projects. Each example is published to the site as a full example report, with details, code, links, and further images in each.

### Textures & Core Concepts

The basic setup for a deep painting is that you have a canvas, which can be modified at will by the AI process, to match a particular signal. This signal matching network consists of a filter, which modifies the image into more abstract data, and then a loss function which measures how close that data signal is to a reference (i.e. style) signal. These filters and operators can then be scaled and combined to form a limitless variety.

#### Pipelines and Layers

A pipeline is a pre-trained deep vision network which is loaded and made available as a series of image processing layers. Each layer builds on the last to extract higher-level details from the source image. This can be illustrated by this example which surveys the sequence of layers in the VGG19 pipeline, using each layer to reconstruct a target signal.

![](../../img/bebe99ad-56ec-4066-957a-25a3dc4c99d1.gif)

#### Operators - Signal Matchers and Enhancers

You can also configure operators, which define how close a signal is to the objective. This objective may be some kind of “similarity measure” to compute how close one image is to another, and many such measures exist; these approach zero. Others simply seek to increase a measure, for example rms “power” as used in DeepDream, possibly with some cutoff before infinity. A survey example of them displays the varied effects:

![](../../img/c83f2d58-c3b6-4718-967d-20919d98d29a.gif)

#### Seed Canvas - Noise, Plasma, Image

When a painting process is begun, there must be some data on the canvas to start with. Interestingly, a completely blank canvas produces poor results, due to something called “symmetry breaking”. There are three main types of seed used in deepartist.org: Noise, Plasma, or Image. Noise is simple random white noise, which can be scaled and offset. (For that matter, scaling and offset syntax is available for all image input urls) Plasma is a simple algorithmic texture that resembles a randomly-colored cloud. An actual image can also be given, either as an upload or as a literal url. This example displays a survey of these seed types when used to paint with the same texture parameters:
As you may note, starting from the image results in something that looks like style transfer. This isn’t so much style transfer as warping the content image until it resembles the desired style. Among other differences, it tends to be deterministic - if you run it 3 times, you get nearly the same 3 results.

![](../../img/bcd20b5f-4acd-4c66-ae18-ff097ebac6e6.gif)

#### Resolution Sequence Texture Generation/Operative Resolutions

Another important factor in the painting process is what resolution we perform it at. As anyone who’s fallen from orbit knows, things look a lot different depending on how far away you are. This variety manifests itself in out painting process by the operative resolution, of what resolution we do a painting operation at. You can see the variety caused by the same painting parameters being performed at small scale, at large scale, and using intermittent stages in this example:
Growing a texture from a smaller image results in a naturally more complex and varied large structure, whereas initial painting using a higher resolution typically produces a more uniform look.

![](../../img/36ada47b-09bb-4e9c-be0e-9f1fbaec8063.gif)

#### View Layers

This can be further modified by attaching additional filters to the vision pipeline layers, such as in these examples:
1. Tiled Texture Generation - By wrapping the canvas around itself to enlarge it, we learn to paint regardless of these wrapping boundaries, and will get a tileable image. ![](../../img/1dde3d05-d225-420d-94f1-fdb1c4692429.gif)
1. Kaleidoscope: Rotational Symmetry and Color Permutations - A layer which reflects and rotates space (and color space) can produce an image with a guaranteed symmetry. This can be combined with the tiling layer. ![](../../img/ee374398-0833-46ec-a848-94b48f03f908.gif)
Additionally, the resulting canvas can be post-processed by any other function. One fun example of this is the stereogram generator.
![](../../img/da74d9a2-5c95-4f55-8962-0108c28a970f.gif)

### Style Transfer

Depending on your religion, you may wish to paint a painting to resemble some object or scene. If you insist on your graven images, you can use the content matching operators. These are handled slightly differently than the style operators, but are fully illustrated by the following examples.

#### Content Reconstruction Survey

Content images can be reconstructed by signal matching using any vision layer, in the same manner as style matching. Each level higher conveys less local information, such as color, and more higher-level information such as patterns. You can see this in the following survey, which uses each layer in a pipeline to reconstruct target content without any further modifiers.

![](../../img/f9f3e56e-f61e-40c0-9f56-0ae3207e05c2.gif)

#### Simple Style Transfer

When these content operators are combined with style operators, we can demonstrate classic deep style transfer, such as in this example:

![](../../img/8439dcb8-dd99-449a-be66-2b1e468c2139.gif)

#### High-resolution Multi-phase style transfer

For high-definition results, multiple phases of style transfer processes can be used while progressively enlarging the canvas. By fine-tuning the parameters for each resolution, we can gain better control over the result.

![](../../img/5aa27a64-6b36-47fa-8b1e-9e63cb8a0c63.gif)

### Animations

There are images, there are videos, and in between there are animated gifs. Animated GIFs are one speciality of DeepArtist.org.

#### Surveys

A variety of animations have already been shown, wherein we survey a variety of treatments, and combine them with labels into an animation.

#### Sweeps

Another type of animation is to sweep a range of parameters. One example provided is a style transfer sweep from one style to another:

![](../../img/618be29e-aef5-492a-ba58-3000d8665182.gif)

#### Determinism and Jitter

Why start with white noise when we do a style transfer? Wouldn’t it be faster to start with the content image itself and change it to match the desired style? One reason is that this heavily biases the result in a way you will have trouble controlling, but another is that the result is deterministic. If we start with noise, there is an inherent randomness to our resulting image that makes it unique. If we use this randomness to produce an animation, we get a unique jittery effect:

![](../../img/e677a8ec-ba9b-44af-ab34-d56dd15cd130.gif)

This can also be combined with kaleidoscopic textures:

![](../../img/be5c5fc4-750e-4786-aadc-1442a1e88bf7.gif)

That's the bag of tricks contained in the first release. Enjoy!