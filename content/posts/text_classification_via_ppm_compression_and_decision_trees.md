{
  "disqus_url": "http://blog.simiacryptus.com/blog/text_classification_via_ppm_compression_and_decision_trees/",
  "disqus_title": "Text Classification via PPM Compression and Decision Trees",
  "Title": "Text Classification via PPM Compression and Decision Trees",
  "Pubdate": "2017-03-27",
  "Keywords": [
    "Decision Trees",
    "NLP"
  ],
  "Tags": [
    "Decision Trees",
    "NLP"
  ],
  "Slug": "text_classification_via_ppm_compression_and_decision_trees",
  "Section": "post",
  "comments": true
}

Text classification is a common machine learning task which is known in various contexts as sentiment analysis, language detection, and category tagging. Many standard AI tools can be used on text given an appropriate feature selection function, which essentially transforms text down into a high-dimensional vector. However there are also certain techniques that work directly on the text, and this article is about a couple of those techniques that are enabled and demonstrated by the new release of the [CharTrie](https://simiacryptus.github.io/utilities/java-util/apidocs/com/simiacryptus/util/text/CharTrie.html) component of the [SimiaCryptus utilities library](http://mvnrepository.com/artifact/com.simiacryptus/java-util).

We [previously](http://blog.simiacryptus.com/2017/03/text-modeling-compression-and-markov.html) discussed the CharTrie library and various ways to use it, including analyzing text and generating shared dictionaries for LZ-type compression and being used directly for PPM-type compression. However, the effectiveness of both of these compression techniques depends on the text being compressed resembling the text used to generate the compressor... But as Grandma used to say, that’s not a bug, it’s a feature! It turns out we can take several texts, train a compressor on each, and then test new text by seeing which compressor produces the most compact output text. 

If we are using LZ compression with a shared dictionary, then more strings the dictionary shares in common with the text means a smaller output - however, this is in practice not a very effective form of categorization for a variety of reasons. Mainly, the shard dictionary only primes the compression, and has little effect after many kilobytes of data.

If we use PPM compression, though, our categorization results are much better. This is actually an extremely effective language detection method, even with a fairly short tree depth/chain length as shown in the “[Language detection using PPM](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.TrieClassificationBlog/language_detection_ppm.md)” notebook. We might expect this intuitively if we consider that the Markov chain output for a tree even 4 or 5 deep has a recognizable source language even if many of the “words” are gibberish and there is no real content. As in many AI techniques, the choice of various meta-parameters is critical, but even with short models reliable language detection is enabled. In testing the small prepackaged language models in this notebook (each about 300k in storage), we demonstrate almost 100% discrimination with the notable exception that about 10% of German text is labeled as French.. To provide this functionality for convenient use, we have also packaged several [pre-built](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.LanguageModelBuilder/buildLanguageModels.md) language [models](https://github.com/SimiaCryptus/utilities/blob/master/java-util/src/main/java/com/simiacryptus/util/text/LanguageModel.java), with the effectiveness demonstrated in [this notebook](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.TrieClassificationBlog/prebuilt_language_models.md).

PPM compression efficiency, however, performs poorly for categorizing other data sets. For example, in this “[Sentiment Analysis via PPM Compression](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.TrieClassificationBlog/sentiment_analysis_ppm.md)” notebook we see almost no predictive capability for discriminating positive and negative tweets; around 50-60% accuracy for a binary variable. To improve on this, we have developed a maximum-entropy splitting function that determines, for a set of categorized strings, the ideal sub-string to search for such that the now-split collections have maximally biased class distributions. This is of course the basic principle used for partitioning a decision tree, and we have also provided a recursive method to generate a very simple decision tree from this partitioning rule. This method is demonstrated in the “[Sentiment Analysis using Decision Trees](https://github.com/SimiaCryptus/utilities/blob/master/java-util/reports/com.simiacryptus.util.text.TrieClassificationBlog/sentiment_analysis_ppm.md)” notebook, which illustrates both the moderate (60-80%) efficacy and the transparent rule set structure decision trees are known for. Note that this particular rule set has extremely fuzzy labels that even a human would not reliably agree with, so the results are somewhat anecdotal without a larger survey.

Examination of an example decision tree shows that the rules are commonly recognizable word fragments with a definite association - rules matching “hanks” match both “Thanks” and “thanks”, and rules matching “n’t” imply some sort of negation. This illustrates one of the advantages to using this method over a term-vector method - this method can automatically work on word parts, stems, conjunctions, and other local non-term features. This unification can potentially simplify the text modeling process.

Further improvements could be made with e.g. a random forest model, and of course there are many other potential uses exist for CharTrie-based text analysis. Avenues I have been exploring include spell correction, keyword extraction, and tokenization. In short, this is just a sample demonstration of what is hopefully a very useful tool. Enjoy!

