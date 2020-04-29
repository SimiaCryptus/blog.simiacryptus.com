{
  "disqus_url": "http://blog.simiacryptus.com/blog/tensorflow_and_java/",
  "disqus_title": "TensorFlow and Java",
  "Title": "TensorFlow and Java",
  "Pubdate": "2019-01-22",
  "Keywords": [
    "TensorFlow"
  ],
  "Tags": [
    "TensorFlow"
  ],
  "Slug": "tensorflow_and_java",
  "Section": "post",
  "comments": true
}

I have been looking at TensorFlow again, after a couple of years, and I was very pleased to see there is now an [official Java release](https://www.tensorflow.org/install/lang_java) of the API, interop, and native binaries. These are all [published to maven](https://mvnrepository.com/artifact/org.tensorflow/tensorflow/1.12.0) and easily loaded into the process using the standard Java API. Hurray!

However, I quickly ran into limitations. The API gave a bridge to the native runtime, so you effectively have the functionality of the C++ API within Java, but the C++ API doesn’t do everything. For example, if you want all the details of graph contents, you need to parse the protobuf graph definition. It does include some pure Java helper classes for graph construction, but that must be newer than the examples, which don't use it.

Unfortunately, there are some important parts of TensorFlow which are currently implemented using Python. One of the banner features of TensorFlow is Tensorboard, which is a UI implemented completely in Python (and JS/HTML/CSS). Additionally, the optimizer code used to actually train models is all Python. The heavylifting code that calculates the forward and backprop/gradient itself is what TensorFlow does natively. This more or less makes sense given this early stage of implementation - The models are developed mainly in Python by data science people, but when deployed these models need to run in a variety of environments with production quality. The need to run the tensorflow graphs on consumer devices, after being trained, is the focus.

How can use TensorFlow in a Java environment, where we wish to minimize Python and maintain functionality?

* Tensorboard is Python, but it only consumes records written during training and execution. I have implemented a class to write and read records using pure Java, to be later presented by the normal Python Tensorboard.
* Optimizer code for TensorFlow is written in Python. This provides a wonderful reason for MindsEye to exist and fill a gap - The optimizers I have developed can be used to train models using just Java and native code! I’m wholeheartedly biased, but once implemented this selection will make Java a far preferable environment in which to develop models! MindsEye provides optimization algorithms and features found nowhere else.
* Examples! I will work to expand the collection of demos and examples to solve simple, benchmark, and useful problems. The Java examples provides by the official TensorFlow publications are out of date (they don’t use the Operator class) - It is clear some help is wanted in this area!

In seeing this vacuum, I rushed out release 1.5.1 of the SimiaCryptus Data Science Platform. This includes the module [tensorflow-model](https://mvnrepository.com/artifact/com.simiacryptus/tensorflow-model/1.5.1) and support classes with minimal dependencies (zero native). This release also includes an independent build of the  Java support classes for all the protobuf structures. Since the release, I discovered where to find the [official release's protobuf classes](https://mvnrepository.com/artifact/org.tensorflow/proto).

The current code branch also includes code to read and write tensorboard event logs. Future releases will include examples of how to directly integrate TensorFlow graphs as MindsEye gradient descent components, in particular using MindsEye to direct model training. Unfortunately, the ability to conduct such training on a general TensorFlow graph depends on support for generating gradient operations from existing graphs. This is an area where support was previously only in Python, but for which there is an [ongoing porting effort](https://www.tensorflow.org/code/tensorflow/cc/gradients/README.md). This means that some operations simply do not yet have gradients implemented for them unless using Python. Fortunately, expanding the support for C gradients does look like a reasonable process.

For the time being, example usage of Tensorflow from Java can be view on the latest code of [tensorflow-model](https://github.com/SimiaCryptus/tensorflow-model). The best place to start reading is the [unit tests](https://github.com/SimiaCryptus/tensorflow-model/blob/master/src/test/java/com/simiacryptus/tensorflow/InceptionTest.java). Enjoy!

