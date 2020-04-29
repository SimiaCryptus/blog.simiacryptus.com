{
  "disqus_url": "http://blog.simiacryptus.com/blog/texture_generation/",
  "disqus_title": "Texture Generation",
  "Title": "Texture Generation",
  "Pubdate": "2018-04-09",
  "Keywords": [
    "MindsEye"
  ],
  "Tags": [
    "MindsEye"
  ],
  "Slug": "texture_generation",
  "Section": "post",
  "thumbnail": "../../img/e88bc0c7-e00d-461f-88a7-13ffcc818674.png",
  "comments": true
}

One very entertaining application of deep learning is in style modification and pattern enhancement, which has become a popular topic on the internet after Google’s [Deep Dream post](https://research.googleblog.com/2015/06/inceptionism-going-deeper-into-neural.html) and subsequent research and publications on [style transfer](https://github.com/jcjohnson/neural-style). Reproducing this research has long been a goal for the development of [MindsEye](https://github.com/SimiaCryptus/MindsEye), and now that it is achieved I’m having quite a bit of fun with this playground I built! I have collected the interesting visual results of my work in [this online album](https://photos.app.goo.gl/5SeREKdmYuIzMSv12).

Pattern enhancement, style transfer, and similar effects are new tools based on deep learning that can be applied to an image, but in usage they are just like any other image processing filter. When combined with other components, we can generate or modify images in a carefully designed pipeline; it is the best of these results that you see in published work. This is just like any other image processing pipeline in artistic or computer vision applications in many respects, and many steps have nothing to do with neural networks.

The pipeline we are about to discuss generates tiled textures, suitable for use as texture fill, wallpapers, etc. It works in a fairly simple loop after being seeded by an initial painting process, where the canvas is progressively enlarged while a deep-learning-based model is optimized. This both increases training efficiency and improves multi-scale resolution.

In more detail:

1. The initial canvas is painted using a [diamond-square-fill algorithm](https://en.wikipedia.org/wiki/Diamond-square_algorithm) on a toroidal space. (This is a well known and flexible texture generation method by itself.)
1. The canvas is then processed using one or more steps, each of which is of one of these types:
    1. The texture is optimized so that style vector(s) is/are reproduced by minimizing several distance metrics. (The weight vector used to mix these metrics is a useful free parameter.)
    1. The texture is enhanced so that any patterns that appear (on a given layer) are enhanced. This maximizes the L2 magnitude of the signals on various layers, subject to a weighting vector.
    1. Criteria in (a) and (b) can be mixed by using a signed linear mix
1. After all steps of the iteration are completed, the result is saved, the canvas is enlarged via bicubic scaling, and the process returns to step 2

![](../../img/696734cc-1548-4a30-ae22-1da558de04ed.png)

Step 0/1 - Initial Painting and Style Transfer

![](../../img/7e0b3635-f470-482c-bd43-6d3ead972fc8.png)

Step 2 - Pattern Enhancement

![](../../img/2b1c1144-8bb8-4a1f-9e01-292f0b62bf28.png)

Step 3, etc - Enlarge and Repeat

This is very similar to the classic style transfer algorithm discussed in the paper here, which we’ve also taken some steps to reproduce. The process is very similar to that detailed above, but we also use a distance metric to a “content” image to guide our painting process. This largely depends on the weighting between the style criteria and the content criteria. Assorted examples of the product follows:

![](../../img/c11eeacb-8336-4e32-8f4f-3137223180b3.png)
![](../../img/51bf1a58-ae2c-4d30-9aa6-e9cb5a6a6b53.png)
![](../../img/9be29f47-4aa3-4d96-90da-fa5f92ae96af.png)
![](../../img/dd67054e-ea55-40e3-81da-87c4af5402b8.png)
![](../../img/e88bc0c7-e00d-461f-88a7-13ffcc818674.png)

Well, I hope you found this interesting! If you’d like to generate some artwork of your own, it is easy to clone and run! The notebooks used in this post are here and here; all that is required is Java, CUDA, and CuDNN! Look for my next post where I will discuss running these applications on the AWS cloud, leveraging the Deep Learning Base AMI and P3 gpu-accelerated instances...

