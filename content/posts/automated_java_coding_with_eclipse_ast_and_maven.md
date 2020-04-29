{
  "disqus_url": "http://blog.simiacryptus.com/blog/automated_java_coding_with_eclipse_ast_and_maven/",
  "disqus_title": "Automated Java Coding with Eclipse AST and Maven",
  "Title": "Automated Java Coding with Eclipse AST and Maven",
  "Pubdate": "2020-01-11",
  "Keywords": [],
  "Tags": [],
  "Slug": "automated_java_coding_with_eclipse_ast_and_maven",
  "Section": "post",
  "comments": true
}

I have always contended that there are three things that have made Java the most successful language of our time:
1. __Open source__ - Lawsuits against Microsoft and Google aside, Java’s community process, conventions, and general open-source nature have made development on this platform a largely white-box affair. If you aren’t sure why a library is not working the way you want, it is almost always possible to dig into the source code. Documentation usually sucks, but source doesn’t lie.
1. __Strongly-Typed, yet Simple__ - These two items are generally a trade-off, but Java treads a narrow path combining both simplicity and rigor. It is always clear in Java what fields and methods are available in a given object. This allows development tools to be very powerful and reliable. On one side of this narrow path is Scala and C++, providing a strong type system but with a syntax so complex that tool development and developer expertise becomes much harder and more expensive. On the other side you have Python and Visual Basic, which delight in readability but over time become hostages to their own legacy.

This is why I love the Java platform, and why the community loves it. It is why it dominates server and business applications, and why Android uses it so heavily. A good Java developer can work with HUGE amounts of Java source code with confidence, producing so many changes that it becomes hard to keep up with in a manual review process. Consider how easy it is to rename a field or method, not to mention the other advanced refactoring tools freely available. These tools often make coding very similar to working with mathematical equations, a centuries-old tradition which seeks elegance in expression and beauty in truth. As a physicist by training, I highly value these concepts.

The potential of this power, though, extends far beyond general refactoring tools. I worked for a certain company a while ago where I used this capability to define complex yet reliable automated coding tools to ensure that between every call from a web service layer to a database layer, there was a caching layer involved. I am currently using these capabilities to produce [automated coding tools](https://github.com/SimiaCryptus/java-reference-counter/tree/master/refcount-autocoder) to assist with reference-counting lifecycle management, which heretofore have been coded manually in [Mindseye](https://github.com/SimiaCryptus/mindseye-core). The subject of reference counting and it’s place in Java has been previously written about in this blog, and a follow-up will be coming soon, but for the time being I’d like to introduce the base component that makes it easy to develop automated Java coding tools.

This base library, [autocoder-core](https://github.com/SimiaCryptus/java-reference-counter/tree/master/autocoder), imports a library published by Eclipse and combines it with Maven to provide a very easy way to analyze and edit the source code of any Java Maven project. Simply import the library, define a class deriving from AutoCoderMojo, add an attribute to name it, and then define one of more editor classes, which use Eclipse’s AST visitor model. A simple example is available as [PrintAST](https://github.com/SimiaCryptus/java-reference-counter/blob/master/autocoder/src/main/java/com/simiacryptus/ref/core/PrintAST.java), which simply outputs all nodes parsed by the Eclipse Abstract Syntax Tree (AST). Any edits made to the object model of the Java source code will be written back into the source code with minimal changes. Your code can then be run using Maven, or programmatically invoked using an embedded version of Maven. For example, PrintAST can be run (once a build has installed it locally - no public release has been made yet to the maven repos) via:

```
mvn com.simiacryptus:refcount-core:printAST
```

Though similar capabilities have existed for some time, this method integrates with a command-line build tool (Maven) and happily works outside any IDE. I hope it is useful to some of you - the creative possibilities are vast!

Cheers,
   Andrew
