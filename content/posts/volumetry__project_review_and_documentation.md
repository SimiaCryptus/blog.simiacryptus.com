{
  "disqus_url": "http://blog.simiacryptus.com/blog/volumetry__project_review_and_documentation/",
  "disqus_title": "Volumetry - Project Review and Documentation",
  "Title": "Volumetry - Project Review and Documentation",
  "Pubdate": "2015-06-21",
  "Keywords": [
    "Decision Trees"
  ],
  "Tags": [
    "Decision Trees"
  ],
  "Slug": "volumetry__project_review_and_documentation",
  "Section": "post",
  "thumbnail": "/img/55676226-1146-4887-a7ae-a84ff0be30df.png",
  "comments": true
}

Happy Fathers Day!

I've just finished up a review of the next project in my queue: [Volumetry](https://github.com/acharneski/volumetry). The readme on github has a bunch of pretty pictures now and should be helpful to anyone interested in the research. If it looks interesting, I encourage you to run the code yourself; the 2d images aren't nearly as interesting as the 3d models.

Included below are some snippets from the new documentation:

# [testModelProject](https://github.com/acharneski/volumetry/blob/master/src/test/java/com/simiacryptus/probabilityModel/Demo.java#L45)

Displays a modeled "snake" distribution, which is based on a gaussian kernel extruded along a random spline. Demonstrates both slicing and projection operations, where a multidimensional model is projected, or flattened, along some axis to obtain a [marginal density](https://en.wikipedia.org/wiki/Marginal_distribution)

![](/img/7b98cb3a-1c90-495a-aede-14c017ad92df.png)

# [testVolumeEntropyModel](https://github.com/acharneski/volumetry/blob/master/src/test/java/com/simiacryptus/probabilityModel/Demo.java#L189)

This demonstrates the effectiveness of this model-building technique applied to the "3d logistic map".

![](/img/020bf1aa-d46c-4457-ab58-fe019e072d55.png)

# [testSurfaceFiller](https://github.com/acharneski/volumetry/blob/master/src/test/java/com/simiacryptus/probabilityModel/Demo.java#L91)

This demonstrates a unique application of the modeling technique, wherin we wish to find an equipotential surface. This is different from most optimization and numerical solver techniques since it not only has to converge on the solution, it has to fill and uniformly sample all applicable space as well.

![](/img/55676226-1146-4887-a7ae-a84ff0be30df.png)