{
  "disqus_url": "http://blog.simiacryptus.com/blog/the_many_uses_of_word2vec/",
  "disqus_title": "The Many Uses of Word2Vec",
  "Title": "The Many Uses of Word2Vec",
  "Pubdate": "2017-10-12",
  "Keywords": [
    "NLP"
  ],
  "Tags": [
    "NLP"
  ],
  "Slug": "the_many_uses_of_word2vec",
  "Section": "post",
  "comments": true
}

One artificial intelligence tool that I’ve been playing with lately is an algorithm called word2vec. The basic idea is that words are given positions in high dimensional space, and the positions are optimized such that word distance indicates how often words are seen together. These numbers can then be used in a variety of ways, from a simple word similarity search to recurrent neural networks. In this article I will outline some uses of this amazing approach, along with links to sample code and results.

# Modeling

The first thing we need to do is obtain our model. You can mine your own from a text corpus using a tool such as Spark ML’s Word2vec implementation, or you can load  previously-built model. Surprisingly, Spark-ML’s word2vec library uses a local memory object for the model, which makes exploiting it fairly unscalable. It is best to load the vectors into an RDD for scalable analysis once the modeling phase is completed. If you are going to build your own model using Spark ML’s word2vec, here are some parameters to be aware of:

* __Partitions__ - This option determines how many partitions to break the data into when model training in parallel. This defaults to 1, but for even moderate data sets you may want to increase this to the number of machines in your cluster to obtain better CPU utilization. There is an accuracy trade-off to higher partition numbers.
* __Neighborhood Size__ - This determines the window size for the term-relation data gathering. At S=5, any words relations closer than 5 words apart will be counted.
* __Dimensions__ - This is the dimensionality of the model space that the vectors reside in. A higher dimension supports more complexity, but takes more data to train accurately.
* __Minimum word count__ - This is the minimum # of word occurrences for a term to be considered part of the model. Keep in mind that the number of distance constraints needed to fully determine a point’s location is equal to the dimensionality (minus one). Thus, this should be at least DIMENSIONS / NEIGHBORHOOD.

An easier approach is to load one of the pre-trained open source models published by Google, Facebook, or others. [Google’s models](https://github.com/mmihaltz/word2vec-GoogleNews-vectors) are based on Google News crawls, and [Facebook’s](https://github.com/facebookresearch/fastText/blob/master/pretrained-vectors.md) are based on Wikipedia. For both models, I have implemented [parsing/import code](https://github.com/acharneski/ImageLabs/blob/blog-2017-10-07/src/main/scala/interactive/word2vec/SparkLab.scala#L310) to convert these models into a parquet data table. The parquet format is partitioned to allow for scalable processing and is popular in the Spark community.

# Analysis

Once we have derived or loaded a model, what can we do with it? There are a number of use cases, and for each there are analogous geometric entities. Though these entities can often be described as common 2d shapes such as circles and lines, we must keep in mind that we are actually dealing in a high dimensionality. Here are some some effects to keep in mind:

1. Any two random vectors are expected to be close to a right angle to each other (Corollary: The average magnitude of each component of each vector is small, since it is close to a right angle with each axis.) This is a fundamental result of high-dimensional geometry.
1. There is a maximal distance two vectors can be to each other - the continuum is bounded. This is because we are dealing with unit vectors, whose topological manifold is a ball.
1. For N up to D, we can fit a linear entity to span N points. This gives us a convenient way to define regions based on any small collection of points, i.e. the distance to the intersecting hyper-plane.
1. Traditional indexing doesn’t work for these points. Even geometric indexes such as kD-trees are of very limited use, though there are some special methods. Searches and other operations therefore generally have to scan the entire dataset. This makes working with the data very sensitive to scalability and performance problems.
1. This is a proper metric space. One important property of a metric space is the triangle inequality. This condition guarantees that a direct connection between two points is always at least as short as the distance of a path going through a third point.

Many of the methods discussed below are demonstrated in a Spark notebook with source code, Examples, where given, are taken from [this notebook](https://simiacryptus.github.io/www/word2vec/).

# Explore with TensorFlow Projector

A spin-off of the TensorFlow project, Projector is a beautiful tool for visualizing high dimensional points with metadata. I have used it to generate [sample point clouds](http://projector.tensorflow.org/?config=https://simiacryptus.github.io/www/projector-config.json), related to politics, emotions, and geography. The UI allows the reader to explore in three dimensions various concepts matching a particular query. Within this interactive 3D view, you can enhance structure with T-SNE, drill down into sub-populations, and experiment with many other features.

# Find similar terms

The first and most obvious analytical use of this model is to search for synonyms - the points closest to a given point are generally seen near the same words as the base word, thus encouraging secondary co-location effects. This means that the nearest points might not have even directly ever been seen together, but we can still be confidant there is some semantic similarity.

What if we have multiple points, and we want to find a list of words associated with them? To evaluate this query, you need to define a distance metric for the cluster. This could be the sum of distances to all members, or the minimum or maximum distance, for example; this would be known as a power law. Another method, which seems to have given me better results in my limited testing, is to use a hyperplane intersecting the input points; the closest distance to this plane then forms the needed distance metric.

# Unsupervised Clustering

When considering a large group of points, we can use various clustering algorithms to structure the data for further use. This will partition space into a high-dimensional polyhedron (i.e. a polytope.)

# Cluster Sorting

When examining a single cluster, you may wish to sort the members to better characterize them. For example, the sum of all distances to each node from one given node will give a measure of the point’s interior/exterior position. This can be used in outlier detection, for example. Another way to sort a cluster is to pick two points, perhaps the pair with the largest distance, to define an axis along which to sort.

# Putting it Together - Word Taxonomy Generator

We can combine the above three concepts into a single interesting demo. Our application takes a list of terms, and returns a tree-formatted listing of related words, organized by category and degree. First, we select a point population using the distance-to-intersecting-plane method, and then we apply a recursive clustering algorithm on it to break our initial large word list into a more structured tree. Nodes are then ordered according to average distance-to-plane, and terms within a single tree node are sorted using the two most distant points to define the axis. The result is a great deal of self-organization in the output, automatically inferring relevant sub-categories based on the selected subject matter. For full output generated by this method, see the research notebook published on github.

For example, upon generating a word taxonomy for emotional words based on "happy", "sad", "laughing", "crying", "depressed",  and "excited". One of the output tree nodes are:

1. Cursing
1. Uttering
1. Swearing
1. Muttering
1. Booing
1. Yelling
1. Crowd
1. Chanting
1. Jeering
1. Shouting
1. Cheering
1. Cryings
1. Waving

Notice how it is automatically ordered by the positivity of the expression listed.

# Word Spectrums

Another way to combine the above on pets is to generate a word spectrum; Given two input words, we can find all words that lie more or less directly in between the words, and sort them by which end they are positioned nearest to. This results in a list of words bridging one extreme to another. The distance metric used in this method is very similar to the equation that defines an ellipse. This allows suggests an interesting way to explore the term network, as you can list synonyms “in the direction of” another word.

For example, a list of terms from ”happy” to “sad” follows. The first coefficient is the position along the spectrum. The second is how close the term is to the axis - how nearly in-between the other words this word is.

1. happy → 0.000 / 0.000
1. happily → 0.393 / 0.800
1. ~happy → 0.399 / 0.886
1. —happy → 0.403 / 0.883
1. happy, → 0.420 / 0.873
1. shappy → 0.421 / 0.880
1. happier → 0.423 / 0.762
1. delighted → 0.434 / 0.880
1. thrilled → 0.442 / 0.813
1. wonderful → 0.448 / 0.884
1. thankfuly → 0.457 / 0.925
1. nice → 0.462 / 0.928
1. happinesss → 0.465 / 0.898
1. honest → 0.468 / 0.892
1. happiest → 0.469 / 0.859
1. cheerfully → 0.469 / 0.915
1. unhappy → 0.470 / 0.883
1. happiness… → 0.471 / 0.913
1. worriesome → 0.471 / 0.922
1. cheerful → 0.475 / 0.853
1. regretfully → 0.475 / 0.917
1. lovely → 0.476 / 0.846
1. happy/sad → 0.478 / 0.924
1. saddend → 0.484 / 0.902
1. loved → 0.489 / 0.916
1. regrettfully → 0.490 / 0.891
1. regretful → 0.492 / 0.816
1. disappointed → 0.494 / 0.901
1. heartening → 0.494 / 0.914
1. heartwarming → 0.496 / 0.872
1. dishearten → 0.496 / 0.908
1. lonely → 0.496 / 0.924
1. remember… → 0.496 / 0.929
1. saddens → 0.497 / 0.879
1. trouble… → 0.498 / 0.905
1. saddened → 0.498 / 0.930
1. sadden → 0.499 / 0.925
1. funny → 0.501 / 0.930
1. dishearted → 0.502 / 0.886
1. disheartening → 0.502 / 0.907
1. regret → 0.506 / 0.911
1. disappointedly → 0.506 / 0.929
1. dishearteningly → 0.506 / 0.907
1. miserable → 0.516 / 0.854
1. saddening → 0.521 / 0.868
1. saddest → 0.526 / 0.903
1. sadder → 0.527 / 0.868
1. sadness → 0.537 / 0.920
1. pathetic → 0.538 / 0.858
1. sad → 1.000 / 0.000

# Word Analogies

This ability is surprising to most when they first learn of it. It allows for solving word analogies based on vector math by completing a parallelogram. “Boy” is to “Girl” as “Man” is to Woman” Becomes “Girl”-“Boy”+”Man”=“Woman”. Though it is often hard to explain why this works, in practice these analogy solutions have become a standard way to benchmark models.

I have provided a few examples of these analogy problems solved in the research notebook, such as:

boy is to girl as man is to...
1. woman → 0.253
1. woman—who → 0.322
1. thug → 0.333
1. man— → 0.344
1. gangster → 0.346
1. policeman → 0.347

wait is to waiting as run is to…
1. running → 0.048
1. ran → 0.139
1. runs → 0.182
1. runnings → 0.186
1. running → 0.271
1. runnoff → 0.310

# Machine Translation

Early in the 20th century, archeologists had documented much hieroglyphic text, but were unsure of any translation. Then they discovered the Rosetta Stone, which provided a sample translation to relate this language to known ones. With this key, the rest of the language was able to be inferred. Today, we can automate this process with math and computers! This may come in handy if we ever need to analyze an alien civilization’s Wikipedia, the exchange of which might actually serve as a “handshake” during first contact.

This type of machine translation alone will not render the ability to translate one sentence into another language - that is far more advanced cognitive process - but this is an important component. It allows us to learn a translation function based on a limited number of translation examples, which can then suggest new single-word translations. This function is generally a simple linear matrix-multiplication operation, and can be modeled very efficiently.

For example, if we took two corpuses of text in two different languages, we could build a word2vec model of each language. Given a reasonable sample of term pairs, we can then attempt to derive a transformation matrix from one term-space onto the other using standard linear algebra. Once this is derived, we can search for approximate word translations using a nearest-neighbor search. This would only be one component of a full translation pipeline, of course, but an important one.

That concludes today’s tour of word2vec use cases. Of course, there are many other possibilities to use this data... Have Fun!

# Suggested Research Problems:

1. Derive a translation metric using the Facebook Wikipedia models for two or more languages and some seed word translations. Test it against a control sample of valid translations.
1. Devise a normalization scheme to normalize an abribrary language vector model so translation matricies are always close to the identity matrix. Demonstrate the efficacy of this universal language translator.
1. For all words in a model, generate a “nearest cluster” set of words that are the N-nearest to each base word. Analyze the scalability of your method.
1. Transform two or more language models such that they are aligned for translations. For all words in the models, generate a “nearest cluster” set of word translations that are the N-nearest to each base word. Analyze the scalability of your method.
1. Generate a full clustering hierarchy of all terms in a Facebook/Wikipedia model. Run this process several times and analyze stability.
