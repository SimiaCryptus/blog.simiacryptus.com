{
  "disqus_url": "http://blog.simiacryptus.com/blog/eye_candy/",
  "disqus_title": "Eye Candy!",
  "Title": "Eye Candy!",
  "Pubdate": "2018-04-01",
  "Keywords": [
    "MindsEye"
  ],
  "Tags": [
    "MindsEye"
  ],
  "Slug": "eye_candy",
  "Section": "post",
  "thumbnail": "/img/cb99788b-4592-4444-854b-7536a5b0d39d.png",
  "comments": true
}

Deep Learning has in recent years seen dramatic success in the field of computer vision. Deep convolutional neural networks tens of layers deep are becoming common and are some of the best performers for image recognition. Additionally, these learned networks can be used to produce novel artwork, as seen in recent publications about Deep Dream and Style Transfer. Today we will explore these applications with our own neural network platform, MindsEye.

At the core of this image-processing functionality is the pretrained image recognition network. In our initial version we use VGG16, a standard open-sourced network trained to classify the ILSRCV2011 dataset. Other networks can be used, and out-of-the-box support for additional networks will be added in the future. We will discuss two different uses of these models: First, we will discuss image recognition including multiple objects and locating objects within a picture. Then, we explore computer-generated artwork using techniques based on the Deep Dream and Style Transfer papers.

## Object Detection

A common task for working with images is to identify objects, both type and location. This describes the OCR process used to scan documents, and also a key ability of autonomous vehicles. We will demonstrate how to use a variant of the VGG-16 network on a test photo with multiple objects. (This variant will accept images of any size.)

Let’s take a photo and pass it through our classification network. Since we are interested in identifying several objects and we know each object can be assigned significant probabilities in multiple classes, we will take a large sample (the top 20) of the results:
Now, for each top-N detected class, we can back-propagate a signal to estimate the image regions associated with each class. These produce a number of image masks, many of which overlap and are fairly rough indicators of location. We then take these first-order masks and perform PCA analysis to derive a collection of “principle masks”. Each principle mask can then compute it’s own top-N classification result, thus providing both object location and classification.
		
![Source Image](/img/66e72de5-5d7a-42cc-ac00-47cf49fb3071.png)	
![Eigendog](/img/17ea6db0-adb4-4d15-af03-e45fbd3534c8.png)
![Eigencat](/img/6b7f36d5-fd30-4f20-9863-dd93bd40b222.png)

## Computer-Generated Art

In recent years there have been fascinating new results in image generation powered by deep CNNs. These techniques rely on the fact that lower layers of a deep network will learn to respond to textures and shapes, which are then used by later layers for object classification. We can use this transform to define an interesting fitness function for an image, and then use back-propagation learning to generate the image.

![](/img/b4106034-ac53-4d5b-9072-f9d268ac9eb3.png)

The first class of fitness function were originally explored in Google’s Deep Dream paper. We simply take some intermediate level signal, presumably containing shape and texture information relevant to a particular scale, and maximize the L2 magnitude of the signal. This has the effect of back-propagating a reinforcement signal proportional to whatever is detected, directly enhancing patterns. Applied to lower layers, it tends to enhance texture information. Applied to higher levels of networks, this can even make objects appear out of thin air!

![](/img/cb99788b-4592-4444-854b-7536a5b0d39d.png)

The next class of function actually consists of pairs of fitness functions to achieve artistic style transfer. Starting from random noise, we learn an image whose texture signal at a given layer is compared with a given “content” image using RMS error; we are thus reconstructing our image using the higher-order information such as textures and shapes. We add to this the other term in our pair, which compares the signal to a style image after applying a transform which summarizes the signal prior to comparison. This summation function first computes the gram matrix for each pixel, then takes the average value by-component over the entire image. The effect of this is to encourage the generated image to have the same amount of colors and textures overall, thus achieving style transfer.
