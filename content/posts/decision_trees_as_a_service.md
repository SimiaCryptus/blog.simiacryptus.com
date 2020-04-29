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

I discussed in my previous blog post a distributed software transactional memory library I was implementing in Scala. Being a platform, it is hard to demonstrate without some interesting application running on it. I have thus created a decision tree service - a RESTful api to populate, train, and query decision tree structures.

As the majority of this post will discuss the decision tree service, I would like to emphasize that this is merely a demo application for a research-grade platform. It demonstrates many of the useful features of the reSTM system, such as a scalable, persistent, and transactional data store, and a distributed execution service to manage distribute tasks/futures across a cluster. This platform manages the interaction with the cold storage layer, such as Berkeley DB or Dynamo DB, and provides transparent random access to the data. The platform provides the task management functionality to distribute and persist tasks and their results, and manages interdependent tasks; the application is then able to use a familiar asynchronous api to implement the long-running algorithm. Due to this supporting functionality, the entire decision tree application weighs in at only 1500 lines of code.

This service can support an unlimited number of decision trees, which are created on demand. A tree is configured with a ClassificationStrategy, which can be used to configure on-line training. Alternately, the tree can be configured with a NoBranchStrategy so that it accumulates data without automatically splitting. In either case, data can then be inserted by PUTting items into the tree URL. Explicit branching operations can be performed by POSTing the desired ClassificationStrategy to the tree/node URL. The tree consists of a number of nodes, with each node either being a leaf (Containing a collection of data) or a branch (containing a rule and child nodes). Each tree, and each node on the tree, has a URL that can be used to perform critical operations.

* Tree Operations
    * GET /config - Get the strategy for a tree used in online learning
    * PUT /config - Set the strategy for a tree used in online learning
    * POST / - Uploads new items into the collection. Each item should be a Json-formatted single-level map. Items are combined by string concatenation and then posted in the request body.
    * GET /find?criteria - Locate a node in the tree using the keys/values given in the query string parameters. Will return node information, including node id.
* Node Operations (Root node id is always 1)
    * GET - Gets information about the node, including parent path, children, and the id of each.
    * POST /split - Performs an explicit recursive split operation. This will return the ID of a newly created task, which can then be monitored by /tasks/ID/info and /tasks/ID/result
    * GET /list?cursor=0&amp;max=1000 - List a page of items, returned as a json array. The last element in the array is the ID of the cursor to use to get the next set of items.



To demonstrate with some data, I have included a utility that uploads the USGS Forest Cover dataset, often used as benchmark for classification system. The following script shows how to download the application, run the service, upload the data, and perform a demonstration query.

```shell script
# Download the project and test data
curl https://archive.ics.uci.edu/ml/machine-learning-databases/covtype/covtype.data.gz -o covtype.data.gz
git clone https://github.com/acharneski/reSTM.git 
# Build the project
cd reSTM 
chmod +x ./bin/activator 
./bin/activator clean dist
# Start the server
unzip target/universal/play-scala-1.0-SNAPSHOT.zip
cd play-scala-1.0-SNAPSHOT/
bin/play-scala -J-Xmx4g -Dplay.crypto.secret=abcdefghijk  &gt;restm.log 2&gt;restm.log.err &amp;
# Initialize the server
sleep 3
curl http://localhost:9000/sys/init
# Run the test application
cp ../../covtype.data.gz ./
java -cp "conf/:lib/*" -Xmx2g util.DTTestUtil http://localhost:9000/ 10000
```

The test utility will upload the USGS Forest Cover dataset and train a decision tree. Near the end it will display a number of example links that can be called to query the database in the context of a classification task, along with the responses, such as:

```shell script
GET http://localhost:19001/cluster/d6a95c37/find?Aspect=267.0&amp;Elevation=2684.0...
{
   "path":{
      "node":{
         "id":{
            "id":"103079841223:0:e158"
         }
      },
      "treeId":16727,
      "parent":{
         "node":{
            "id":{
               "id":"102738621180:0:66ba"
            }
         },
         "treeId":5576,
         "rule":"Horizontal_Distance_To_Fire_Points &gt; 5001.0",
         "parent":{...}
      },
      "counts":{
         "1.0":1,
         "2.0":11
      }
   }
```

Correct: 2.0 correctly predicted in leaf 16727 with label counts (2.0→11,1.0→1)

The number of correct predictions are shown at the end, but with a single decision tree one should not expect state-of-the-art efficacy. I get around 70-75% for a typical competitive tree trained on 10k items in 7 minutes on my machine.

Decision trees are known as “weak” classifiers. That is, they are not expected to be very effective. This can be greatly improved with what is known as Random Forests - a multitude of trees are grown, and predictions use the average result of each tree. Decision trees are uniquely attractive because they provide inspectable models - you can typically understand all the rules used in plain English.

This decision tree application combines elements of a database (you can store and later reliably retrieve items) with a self-organizing structure that can be used in many ways. It can serve as a classical decision tree in a random forests algorithm, which is known as one of the best performers for many classification tasks. It could also be used for similar item queries, such as spell checking and web searching, with a suitable ClassificationStrategy. The strategy, which determines what rules to create at each node given the known data, determines a great deal about the behavior of the tree. The provided implementation will maximize the co-entropy of the categories given.

This project involves quite a few different components, but I’ve tried to keep it as basic as possible. With so many important features, aspects, and problems to discuss, I couldn’t possibly address them all here. For more information, please see the reSTM User Manual:
