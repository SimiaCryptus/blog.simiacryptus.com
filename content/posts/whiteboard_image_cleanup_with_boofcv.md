{
  "disqus_url": "http://blog.simiacryptus.com/blog/whiteboard_image_cleanup_with_boofcv/",
  "disqus_title": "Whiteboard Image Cleanup with BoofCV",
  "Title": "Whiteboard Image Cleanup with BoofCV",
  "Pubdate": "2017-04-19",
  "Keywords": [
    "CV"
  ],
  "Tags": [
    "CV"
  ],
  "Slug": "whiteboard_image_cleanup_with_boofcv",
  "Section": "post",
  "thumbnail": "../../img/f01a54bf-5838-445c-808d-ec26de3af99e.png",
  "comments": true
}


Good morning fellow code monkeys! Today I’d like to talk about computer vision, and how it can be used in a fairly basic fashion to process whiteboard images and improve them. 

This technology is fairly mainstream, but the reader should be warned that Microsoft holds a [patent](https://www.google.com/patents/US8805068) on rectifying whiteboard images, but I doubt it would stand up in court. There are also many other patents that seem similar. As always, make your millions at your own risk. :-P

I’ve been using the excellent [BoofCV](https://boofcv.org/index.php?title=Manual) library to explore some ideas I had about whiteboard image capture, and had very good results. Nearly everything I wanted to do with the image was provided in this library, and I would recommend it. Anyway, any image processing workflow consists of a sequence of steps. Each step may use one or more strategies and may involve one or more metaparameter, this making the task of designing and optimizing this system similar to many other tasks in data science such as machine learning. The thing that makes Computer Vision problems difficult is that it is usually hard to define good quality metrics on which to optimize this system. 

I will illustrate steps of this [CV processing workflow](https://github.com/acharneski/ImageLabs/blob/master/reports/WhiteboardWorkflow/workflow.md) as follows:

* Identify the dominant quadrilateral in the image - This is the meat of what is covered in Microsoft’s patent, as least in my reading. We identify a quadrangle (4-sided polygon) and then transform the image using an equiplanar transform such that the quadrangle becomes our entire rectangular viewport. If one imagines this process animated, it is clear this idea is practically a definition of “obvious” and thus un-patentable, as it is an automatic mental process we all do all the time. Anyway, at the end of this step we will have a whiteboard image, rectangular and cropped.
* Next, we have an image that is often partially whitewashed due to reflection of a light source. Due to varying lighting, we may have a very unclear picture with a very uneven background and no vivid colors. We now want to identify where the various marker strokes might be. To do this, we use a localized thresholding filter to produce a binary image. 
* This binary image is then recombined with the color image reduce background noise, and is segmented into “superpixels” using the rgb image
* Each superpixel is then scanned and various statistics are gathered about it, such as the expected color, the area, width and height. 
* Each superpixel is then categorized to identify all background and foreground regions and the color of each pen marking. The image is repainting using the renormalized pixel colors.
* Now that the image background has been normalized, we crop excess white space

The process will convert this image:

![](../../img/4623a01d-1e3c-4ff9-8141-b82f73873e81.png)

Into an image like this:

![](../../img/f01a54bf-5838-445c-808d-ec26de3af99e.png)

At the end of the pipeline we have an image that is far more appropriate for online use, with pure colors and whites and an intelligent region selection. This is just a rough and naive approach that I came up with as a milestone towards further research, and commercial apps are going to do a better job, but I could see this code being useful if I for some reason had a pile of whiteboard photos on my hard drive.

This type of image processing can be found in Microsoft’s Office Lens and the Android app CamScanner, but it is more interesting to me as a technical toy and a foundation for more ambitious experiments. In particular, I plan to research these topics:

1. __Multiple image registration__ - Stitching images is easy and useful for very large whiteboards, and it is covered in pre-existing tutorials, but I’d like to exploit multiple images to reduce noise caused by the highly specular whiteboard and camera jitter. Theoretically, I wonder if such technology can use maximum entropy techniques similar to that used in the Hubble Deep Field image so that average cellphones can produce high quality page scans.
1. __Image vectorization__ - reduce the image to a series of vectorized strokes, saved in SVG or similar. This opens up a new universe of tools for editing and rendering for the illustration. There are existing image vectorization tools of course, but I’ve found none that are optimized for whiteboard-like drawings. You’d get polygons instead of strokes, for example, and the stroke consolidation logic would be far suboptimal.
1. __Geometric alignment optimization__ - I wonder if a drawing could be improved by identifying things that are very close to geometric primitive arrangements and tweaking the vectorized brush strokes to optimize geometric perfection. Imagine a filter that could make your lines straight and parallel, your lines perfectly intersect, and your circles and squares perfect - sound cool?
1. __Text identification and recognition__ - First, it probably would help to avoid the above step for text entities. Instead they would be recognized and send through a parsing mechanism. This should not only recognize characters, but text strings whose OCR is optimized by HMM.
1. __Movies__ - The ability to take image over time of the whiteboard and generate a gif or PowerPoint or similar with markings changing over time appropriately. This could be combined with webcams and an audio feed to easily produce good lecture content. (Multiple webcams used to accommodate occlusion by the lecturer)
1. __Applying similar logic to paper scanning__. The extra difficulty here is that the writing surface will not be an exact plane. In the case of a scrap of paper, it may not even be rectangular. In another common case, in a book, there is fairly severe distortion near the bindings. These distortions may be partly countered by the highly ordered and exact nature of lines of text in a typical book page, for example. This is also a very good case for using multiple images and high-accuracy alignment

