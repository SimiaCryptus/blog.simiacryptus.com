{
  "disqus_url": "http://blog.simiacryptus.com/blog/partitioned_style_transfer/",
  "disqus_title": "Partitioned Style Transfer",
  "Title": "Partitioned Style Transfer",
  "Pubdate": "2018-06-05",
  "Keywords": [
    "CV",
    "MindsEye"
  ],
  "Tags": [
    "CV",
    "MindsEye"
  ],
  "Slug": "partitioned_style_transfer",
  "Section": "post",
  "thumbnail": "",
  "comments": true
}

Our newest improvements to style transfer have improved results even further, with better quality results that are both artistically more distinctive and more recognizable in content. The first improvement used an additional color transformation step to remove color differences before style transfer, and re-add the difference afterwards using an inverted transformation; without it, the best results would require the style and content inputs have similar color schemes.

The second improvement is much more involved, but essentially involves identifying regions of a given image. Both content and style inputs can be broken down into regions - Each content region can be assigned unique style transfer settings to be used in a combined optimization process, and each style region can be used to define a seperate style pattern. We could for example break both images into foreground and background, and then map the style transfer parameters between foregrounds and backgrounds in parallel, allowing each to be treated somewhat independently. This separated process variation is fairly straightforward, assuming we have specified a way to partition the images.

How can these images be partitioned? This is often done manually, and is one of the key usages of an application like Photoshop. However, we’re looking for an algorithmic solution to build a fully automated pipeline... mathematically, we need a clustering algorithm. (We have an image made of many pixels, and our goal is to assign a fuzzy membership for each pixel to some number of clusters.)

One simple clustering method would be to use the color of each pixel and something like a k-means clustering algorithm using Euclidean distance in RGB color space. Although this can produce decent results, it is only sensitive to the color - additional constraints and parameters can improve the results.

To build on this, we use the tools we have already built for image processing and optimization to perform maximum entropy clustering in a very general manner.  The model is basically a logistic regression (softmax) network which is tuned to maximize global distribution entropy (each category should have a well-distributed size) while minimizing local entropy (each pixel should have clear ownership in a category) according to a particular seed point and set of constraints.




This fundamental clustering is applied directly to the color information, but we can then combine this with higher-level knowledge taken from intermediate layers of a deep convolutional network such as VGG19. Each intermediate signal layer can itself be directly clustered using the same process we used to cluster the color bands of the original image, and these signal clusters can then be backpropagated through the network to derive source image cluster indications. These clustering indicator results, from each layer taken together, are then used in a final clustering process.

When we combine these techniques and tuned the parameters appropriately, the resulting image segmentation does a good job of separating major picture regions such as foreground/background. Fed into our parallelized style transfer process, we produce outwork of much higher quality:

![Result]()

This is in comparison to this image, generated with all the same parameters but without content/style partitioning:

![Result]()

Notice this image has much less style contrast between foreground and background than the previous, for example.

I hope you enjoy these improved results!