{
  "disqus_url": "http://blog.simiacryptus.com/blog/decision_trees_as_a_service/",
  "disqus_title": "Decision Trees as a Service",
  "Title": "Decision Trees as a Service",
  "Pubdate": "2017-01-15",
  "Keywords": [
    "Decision Trees",
    "STM"
  ],
  "Tags": [
    "Decision Trees",
    "STM"
  ],
  "Slug": "decision_trees_as_a_service",
  "Section": "post",
  "comments": true
}
Correct: 2.0 correctly predicted in leaf 16727 with label counts (2.0→11,1.0→1)
```
The number of correct predictions are shown at the end, but with a single decision tree one should not expect state-of-the-art efficacy. I get around 70-75% for a typical competitive tree trained on 10k items in 7 minutes on my machine.

Decision trees are known as “weak” classifiers. That is, they are not expected to be very effective. This can be greatly improved with what is known as Random Forests - a multitude of trees are grown, and predictions use the average result of each tree. Decision trees are uniquely attractive because they provide inspectable models - you can typically understand all the rules used in plain English.

This decision tree application combines elements of a database (you can store and later reliably retrieve items) with a self-organizing structure that can be used in many ways. It can serve as a classical decision tree in a random forests algorithm, which is known as one of the best performers for many classification tasks. It could also be used for similar item queries, such as spell checking and web searching, with a suitable [ClassificationStrategy](https://github.com/SimiaCryptus/reSTM/blob/release_0.1/app/stm/clustering/strategy/ClassificationStrategy.scala#L38). The strategy, which determines what rules to create at each node given the known data, determines a great deal about the behavior of the tree. The provided implementation will maximize the co-entropy of the categories given.

This project involves quite a few different components, but I’ve tried to keep it as basic as possible. With so many important features, aspects, and problems to discuss, I couldn’t possibly address them all here. For more information, please see the [reSTM User Manual](https://docs.google.com/document/d/1NrdFnJWqWfGVvwKLG-WNrsNLir7hp6XkRl5LJFq5sFE/edit?usp=sharing):
