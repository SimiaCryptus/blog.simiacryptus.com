{
  "disqus_url": "http://blog.simiacryptus.com/blog/fun_with_deconvolutions_and_convolutional_neural_networks_in_java/",
  "disqus_title": "Fun with Deconvolutions and Convolutional Neural Networks in Java",
  "Title": "Fun with Deconvolutions and Convolutional Neural Networks in Java",
  "Pubdate": "2015-07-07",
  "Keywords": [
    "CV",
    "MindsEye",
    "Neural Networks"
  ],
  "Tags": [
    "CV",
    "MindsEye",
    "Neural Networks"
  ],
  "Slug": "fun_with_deconvolutions_and_convolutional_neural_networks_in_java",
  "Section": "post",
  "thumbnail": "../../img/7653d555-a5d5-486e-9cef-f0e66c000126.png",
  "comments": true
}

![Restored Image](../../img/eeb05b91-ec1e-4fd3-a950-f82603c819a3.png)

I've gotten to an interesting point in my [latest project](https://github.com/acharneski/mindseye), inspired by Google's fascinating [recent work](http://googleresearch.blogspot.com/2015/06/inceptionism-going-deeper-into-neural.html) with convolutional neural networks. The project can now apply inverse convolution operations using multiple fitness functions.

![Blurred Image](../../img/7653d555-a5d5-486e-9cef-f0e66c000126.png)

I wanted to explore the technology of image processing neural networks from the ground-up, so I started by building the fundamentals of a backpropagation neural network library. Building the basic components and solving the initial problems has been interesting, and surprisingly complex.

My first pretty-picture results are a demonstration of a deconvolution operation, which many people would recognize as a "deblur" operation. This is generally solved in the frequency domain using FFTs, however in this code we solve it directly in the spacial domain using the same learning algorithm used in other neural networks. The deconvolution problem is thus modeled as a [learning task](https://github.com/acharneski/mindseye/blob/blog20151018/src/test/java/com/simiacryptus/mindseye/test/demo/DeconvolutionTest.java#L117).

![Original Image](../../img/791da52b-1b8c-4760-8070-185804b90054.png)

In the images you can see a test image, it's blurred counterpart, the recovered/de-blurred image, and a verification image produced by re-blurring the de-blurred image.

The blurred image shown uses a [5x5 convolution matrix](https://github.com/acharneski/mindseye/blob/blog20151018/src/test/java/com/simiacryptus/mindseye/test/demo/DeconvolutionTest.java#L77), which does not preserve information. That means to reconstruct the image, the program is working with an incomplete set of constraints. The solution is further defined by constraints [against negative-valued regions](https://github.com/acharneski/mindseye/blob/71281ea2c367e017bac1ea25bff44089eb52a0c2/src/test/java/com/simiacryptus/mindseye/test/dev/ImageNetworkDev.java#L67) and a [maximum entropy goal](https://github.com/acharneski/mindseye/blob/71281ea2c367e017bac1ea25bff44089eb52a0c2/src/test/java/com/simiacryptus/mindseye/test/dev/ImageNetworkDev.java#L82).

Deconvolutions have a lot of promise, but as far as I know they have not yet realized that potential in consumer applications. That makes it, for me, a very interesting point between science and engineering.