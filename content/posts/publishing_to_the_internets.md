{
  "disqus_url": "http://blog.simiacryptus.com/blog/publishing_to_the_internets/",
  "disqus_title": "Publishing to the Internets",
  "Title": "Publishing to the Internets",
  "Pubdate": "2017-02-26",
  "Keywords": [],
  "Tags": [],
  "Slug": "publishing_to_the_internets",
  "Section": "post",
  "comments": true
}

Over the past several years I’ve practiced self-publishing my research projects, both by public GitHub archives and via articles on this blog. Doing so required very little effort, and it was important to me that my research be accessible. An interested reader could easily clone and build any of the projects I have discussed in previous articles, and that was good enough.

I have now taken the next step in self-publishing open source software: I have configured maven deployment to the central maven repository, and have also configured and published sites for each module using GitHub Pages. This makes the code and documentation easily accessible by anyone developing in the Java ecosystem, and will significantly lower the barrier to entry for using the software I publish. My hope is that this will enable more practically-focused projects.

Publishing was surprisingly easy due to excellent tools and documentation freely available online. Here is a rough checklist of the tasks I went through, how, and why:


1. Central Repository Deployment - The ability to publish to central
    1. Credentials - Sonatype has a [great walk-through](http://central.sonatype.org/pages/ossrh-guide.html) for how to apply for deployment credentials and configure maven.
    1. Project and POM refactoring - Before publishing you should think hard about your module naming and organization, and make sure it is what you want. In the case of reSTM, I broke it up into several sub-modules. This also includes establishing parent and multi-module POMs to simplify management and organization.
1. GitHub site deployment - Setup the [GitHub maven plugin](https://github.com/github/maven-plugins) and the credentials required. This allows for an easy site deployment to Github Pages and allows the publishing of a variety of project data.
1. Configure site generation - The standard setup I used includes:
    1. [JavaDoc](https://maven.apache.org/plugins/maven-javadoc-plugin/usage.html) / [ScalaDoc](http://davidb.github.io/scala-maven-plugin/example_doc.html) - Code documentation is a primary feature of the module site
    1. [Cobertura](http://www.mojohaus.org/cobertura-maven-plugin/usage.html) - A code coverage testing report, unfortunately I can only get this working for Java projects
    [site.xml](https://maven.apache.org/plugins/maven-site-plugin/examples/sitedescriptor.html) and [pom.xml](https://maven.apache.org/pom.html#More_Project_Information) metadata - Make sure all the field are filled out for a complete site
    1. [Fluido](https://maven.apache.org/skins/maven-fluido-skin/) skin - This skin produces a much cleaner looking site
    1. [Google Custom Search](https://cse.google.com/cse) makes a nice addition to the site, especially to unify your various sites into one search index.
1. To test or run the build, use mvn clean install deploy site.

After some research and setup, I now have nice-looking sites full of information about these projects. Better yet, ongoing maintenance and updates should be relatively effortless for the developer.

So far, I have published five modules:

1. [MindsEye](https://simiacryptus.github.io/MindsEye/index.html) - A neural network library written using Java 8. I implemented it just before TensorFlow was announced, because I found existing frameworks to be somewhat confusing and hard to extend. Plus, it seemed like an interesting exercise.
1. [reSTM](https://simiacryptus.github.io/reSTM/index.html) - An application stack based on persistent cluster memory accessed via an STM-like API. This project was separated into 3 published modules: 
    1. Core - The core component defines the minimal set of interfaces and implementations for storage and transaction logic
    1. API - Defines common transactional collections and a task execution engine; these provide the tools needed to build a practical application.
    1. ML - Implementations of decision trees and (planned) random forests used for classification and similar machine learning tasks.
1. [Utilities](https://simiacryptus.github.io/utilities/java-util/index.html) - Miscellaneous library of components too small to have separate projects but too good not to publish.
    1. Classes for bit-level data storage and manipulation (i.e. Non-byte oriented), useful in bit-oriented serialization code.
    1. Bit-level codec utilities, including hamming codes.
    1. An efficient n-gram index, usable in various text applications such as full text search and Markov string generation. It can create a full text index on 1MB of data in 5s on my machine, with good linear scalability.

I have to say that being present in these new avenues of publishing is far more exciting than I thought it would feel. The benefits, many of which are obvious, added up far faster than I thought… if I had known, I would have done this years ago! Some benefits:

* Publishing lowers the barrier to use for consumers, with instant integration with a variety of build tools and IDEs - Just add a maven/sbt/etc snippet and code away!
* Linkable documentation - This isn’t redundant with the ability to link to source!
* The additional publishing avenues come with SEO and general discoverability benefits, resulting in more usage and higher potential for community involvement.
* Introducing versioned releases and separate modules forces a stricter sense of code discipline.
* Extra services now store your code for posterity, i.e. the central maven repository.
* Separate websites, e.g. [mvnrepository.com](http://mvnrepository.com/artifact/com.simiacryptus), will now index the work and further enhance discoverability.

With this change, I hope to make my research both more accessible and more practically-focused. Stay tuned for useful updates!