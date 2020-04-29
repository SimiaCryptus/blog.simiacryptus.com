{
  "disqus_url": "http://blog.simiacryptus.com/blog/preview_grammar_beans/",
  "disqus_title": "Preview: Grammar Beans",
  "Title": "Preview: Grammar Beans",
  "Pubdate": "2012-01-25",
  "Keywords": [
    "NLP"
  ],
  "Tags": [
    "NLP"
  ],
  "Slug": "preview_grammar_beans",
  "Section": "post",
  "comments": true
}
```

```
<charsequence, charsequence=""><charsequence, charsequence=""><charsequence, charsequence="">
</charsequence,></charsequence,></charsequence,>
```

This can be translated into a grammar very simply:
```
   Grammar<XmlTree> grammar = GrammarBean.get(XmlTree.class);
```

This translation happens according to a number of rules to translate various java types into grammar structures:
* __Terminal Classes__ – Java classes are converted into sequence elements, where each field in the class is an element in the sequence.
* __Super Classes__ – Java classes with the @Subclasses annotation become choice elements.
* __Strings__ – String fields are matched using Regex elements, which are specified by the @Regex annotation.
* __Lists__ – Lists are translated to Repeat elements using the declared generic type
* __Maps__ – Currently maps are only supported for CharSequence values and keys, and are translated using a regular expression with exactly 2 capture groups. The RegexCaptureGrammar element is wrapped with a RepeatGrammar element.
Of course, current support for annotation-driven grammar generation is somewhat limited, but it can be easily extended. The current proof of concept should satisfy many use cases.

# Planned Features

I have many plans for this library, both from a practical and a research standpoint. I am currently working to make this library part of a realtime collaborative code editing website. The idea would be for multiple developers to work on the same code in realtime on the web, with the features you'd expect from a good code editor for your favorite language. To this end annotation-derived grammars need to be able to generate code suitable for gwt compilation, so the language parser can run in javascript. To support efficient text editing, parsing will involve a cache which can be updated with random-access edits such as insertions and deletions. This cache will enable very fast re-parsing of minor text edits by remembering previous grammar matches. More on this later!