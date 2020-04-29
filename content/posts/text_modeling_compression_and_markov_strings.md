{
  "disqus_url": "http://blog.simiacryptus.com/blog/text_modeling_compression_and_markov_strings/",
  "disqus_title": "Text Modeling, Compression, and Markov Strings",
  "Title": "Text Modeling, Compression, and Markov Strings",
  "Pubdate": "2017-03-11",
  "Keywords": [
    "NLP"
  ],
  "Tags": [
    "NLP"
  ],
  "Slug": "text_modeling_compression_and_markov_strings",
  "Section": "post",
  "comments": true
}

The recent wave of publishing and releases included a particularly interesting text analysis component that I’d like to talk about today. There are many possible uses, including text classification, clustering, compression, and creation. Most people would most likely recognize this as the data structure behind Markov strings or full text indexes.

This new component is logically a [Trie Map](https://en.wikipedia.org/wiki/Trie) that counts [n-grams](https://en.wikipedia.org/wiki/N-gram). The idea is that we can break text down into a number of overlapping n-grams, ie N-character strings like the 4-grams “frog” or “n th”. These n-grams are then stored in a tree, so that a node on the 3rd level representing “fro” has a child node labeled “g”; in this way the highly redundant n-grams are stored efficiently and can be looked up.

This library uses a serialized memory format that stores the entire tree as a single blob to avoid object count overhead result from larger trees. As a result, we can easily support large trees with many millions of nodes with very fast operations.

This tool can be used in several ways. One could use the node graph directly to implement [string lookup](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.TrieDemo/demoSearch.md) or other analysis operations, or for many standard use cases this library also includes tools for data generation and compression, entropy measures, and serialization.

# Shared Dictionary Compression

There is a very useful compression method for compressing strings known as “shared dictionary” compression. In general it uses an [LZ](https://en.wikipedia.org/wiki/LZ77_and_LZ78)-type engine, but allows for a pre-loaded dictionary. This approach can bring vast improvements to compression performance for some small documents, providing a compressed but semi-seekable data storage format. This method is fast and available in many environments; in the JRE we can use [Deflater](https://docs.oracle.com/javase/7/docs/api/java/util/zip/Deflater.html). A shared dictionary can also be used by [VCDIFF](https://github.com/ehrmann/vcdiff-java), perhaps as the first stage to pre-compress input into a [BZip](https://en.wikipedia.org/wiki/Bzip2) stream as in [SDCH](https://tools.ietf.org/html/rfc3284). Convenience methods are provided in [CompressionUtil](https://simiacryptus.github.io/utilities/java-util/apidocs/com/simiacryptus/util/text/CompressionUtil.html) to help utilize and demonstrate these algorithms.

This method is very useful when you have large amounts of small-length text documents that need to be individually compressed and randomly accessed. How does one actually generate that shared dictionary, however? We have [tested](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.DictionaryMethodTest/dictionariesShakespeare.md) [several](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.DictionaryMethodTest/dictionariesWiki.md) dictionary generation methods:

A most-common-term based method compiles the most common terms, weighted by several functions including count and length * count with several different penalty values for length to account for encoding/addressing costs.
A classical markov string generated from the language model
A variant of the Markov string generation method intended to generate the most common strings instead of a typical string

Each method has a number of meta parameters and possible variations, and each dataset will respond differently, so in an automated report we explore the effectiveness across each method on a variety of texts and a variety of metaparameters. Initial results show that common-term based methods work pretty well, but a Markov string using a 6-level tree will produce about 20% better results. The specialized dictionary method does better by a further 5%. Keep in mind all of these numbers heavily depend on the dataset you are working with and the metaparameter set, so the serious reader is encouraged to do studies on their own data.

# PPM Text Compression
 
The language model built can also be used directly to compress data using a method called [Prediction by Partial Matching](https://en.wikipedia.org/wiki/Prediction_by_partial_matching). This method can yield very good compression results, but is slower than LZ methods and requires the exact same language model at the decompressing end. This implementation does not support a streaming update of n-gram counts, so the language model must be communicated separately. Additionally, the performance of this method is currently too slow for most uses - about 10kB/sec on my machine. An optimized, native version of this could probably improve this by an order of magnitude or two.

A great example of where this could be used is in a database of tweets; each tweet is small and needs to be randomly accessed, but huge volumes make compression valuable. Tweets generally contain poorly typed and or shorthand messages, and are very short. These factors make other compression methods (including shared dictionaries) less effective than with larger more uniform documents. In our [testing](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.CompressionTest/calcTweetCompression.md), tweets could be compressed to about 80% original size using other methods, while PPM compressed text to an average of 50% size.

To demonstrate PPM compression among other formats, we have produced [notebooks](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.TrieDemo/demoCharTree.md) demonstrating a variety of different compression forms against our test data sets. In short, PPM compression is well suited to small strings where share dictionary methods don't work well, such as with Tweets or URLs. At longer sizes, generics methods have time to “warm up” and quickly become competitive. Shared dictionaries, where competitive for compression efficacy, will have far better performance and are thus preferred.

# Text Entropy and Similarity Measure

Another useful ability is to compare a string to an existing tree, to evaluate how well it “fits” with a given tree. This can be measured by the length of the PPM encoding, or by a more expensive method [measureEntropy](https://simiacryptus.github.io/utilities/java-util/apidocs/com/simiacryptus/util/text/TextGenerator.html#measureEntropy-java.lang.String-double-). This measure can then be used as the basis for clustering, rule generation for decision trees, anomaly detection, and many other purposes.

To demonstrate this measure, I have prepared a couple of examples of text data sets arranged using this metric. The [first](http://projector.tensorflow.org/?config=https://simiacryptus.github.io/utilities/java-util/sentenceClassification/config.json) trains 4 language models, 1 for each of 4 books, and uses them to localize a sample of sentences from the texts. Visible in this data are the entropic basins of each language model, two of which largely overlap. The [next example](http://projector.tensorflow.org/?config=https://simiacryptus.github.io/utilities/java-util/cluster_Wikipedia_PPM/config.json) uses 20 random Wikipedia articles as language models to define 20 measures used to localize a number of other articles, identified by topic title. This data set exhibits clustering around related topics; for example, many scientific or geographic articles are grouped together.

# Tree Serialization and Compression

Even using a serialized array, a large-depth tree will still require a large amount of memory. Fortunately, there is a self-similar structure that can be exploited to serialize the trie very efficiently. When combined with PPM encoding, it can achieve overall compression as a self-contained data format, as demonstrated in [this notebook](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.TrieDemo/demoSerialization.md).

The idea behind this encoding is to divide a tree into successively higher depth “layers”, so you encode the top level “0” nodes first, then the 1st generation children, and so on. Each successive layer of the tree can be encoded using expectation values derived from the previous layer - for example, you can safely assume there are no more”CAT” 3-grams than there are either “CA” or “AT” 2-grams, and none of your nodes use a character that isn’t present in the 1st-level nodes.

As far as I know, this encoding method is novel, and it was actually the topic of research that motivated the original version of this code. I posts about it previously, nearly [2 years ago](http://blog.simiacryptus.com/2015/06/announcing-new-old-project-ubermarkov.html). The implementation offered here emphasizes speed over perfect efficiency, but I may release a more aggressive compressor in the future.