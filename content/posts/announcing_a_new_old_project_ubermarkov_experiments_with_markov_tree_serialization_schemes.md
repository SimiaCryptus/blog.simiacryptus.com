{
  "disqus_url": "http://blog.simiacryptus.com/blog/announcing_a_new_old_project_ubermarkov_experiments_with_markov_tree_serialization_schemes/",
  "disqus_title": "Announcing a new (old) project: Ubermarkov: Experiments with markov tree serialization schemes",
  "Title": "Announcing a new (old) project: Ubermarkov: Experiments with markov tree serialization schemes",
  "Pubdate": "2015-06-18",
  "Keywords": [
    "NLP"
  ],
  "Tags": [
    "NLP"
  ],
  "Slug": "announcing_a_new_old_project_ubermarkov_experiments_with_markov_tree_serialization_schemes",
  "Section": "post",
  "comments": true
}

Happy Friday!

I've just finished reviewing and updating the next project in my backlog of old research to publish. It is an experiment in how to efficiently serialize a Markov tree. I got interested in the idea when exploring some of the curious properties of a Markov tree, specifically one based off a fixed population of N-grams derived from a continuous string. It turns out that most of the data in a piece of text, if not all, can be absorbed into the Markov tree structure and then encoded in the tree's serialized form in a more efficient manner than is obvious for the string itself! I've actually gotten pretty encouraging results from the text compression performance, though not competitive in execution performance.

The project can be found at https://github.com/acharneski/ubermarkov

I will detail the encoding method and benchmarking results at a later time.
