{
  "disqus_url": "http://blog.simiacryptus.com/blog/langtons_ant_and_freinds/",
  "disqus_title": "Langton's Ant and Freinds",
  "Title": "Langton's Ant and Freinds",
  "Pubdate": "2012-01-09",
  "Keywords": [],
  "Tags": [],
  "Slug": "langtons_ant_and_freinds",
  "Section": "post",
  "comments": true
}

Today I will talk about the family of cellular automata related to Langton's Ant. For detailed background I refer you to the excellent articles in Wikipedia, but in short an "ant" is a localized cellular automaton. It has a position on an image, and according to the color at that position it takes an action which modifies its own state, the state of the board, and its position on the board. Over many steps, it will walk around the board and produce various patterns. It can be thought of as something like a two-dimensional Turing machine variant.

In the classic Langton's Ant, the ant has an orientation and at each step it turns left or right depending on if the current pixel is white or black. It then flips the pixel color and steps one pixel forward.

This most-basic ant demonstrates many of the phenomena shown in other ants. It begins with a brief phase of chaotic nucleus-building behavior, where it will form a central area of mixed white-black pixels. Then it will stabilize into an ant trail, where a cycle causes a regular and moving pattern to form. The ant will continue this trail until is reaches something other than a pure-black pixel region, where it generally resume chaotic behavior.

# Color-cycling RL ant codes

Mutli-Colored Ants - Click to view

One generalization of this classical ant is to allow the colors to cycle through a larger loop. So, rather than having a black-&gt;white-&gt;black-&gt;white color transition, you might have a blue-&gt;green-&gt;red-&gt;blue color rotation. With more colors, the ant can make more decisions and we can explore more ant variations. We might express the ruleset for these ants like "RLR" which would mean "On blue, turn right; on green, turn left; on red, turn right".

There are many interesting behaviors in this family of ants. Some create trails, some stay very localized and slowly grow a nucleus with a characteristic boundary, and some fill space with a regular pattern. Some exhibit symmetrical behaviors or various types of self-similarity. Some produce distinctive textures in the space they fill. Some even have complex trail-rewriting behavior, where a previous trail can be encountered and result in a different second-generation trail to form.

The "zoo" on the right shows many such ants, and if you click on a particular thumbnail you will see the ant execute. Click the window again to close the ant; if you leave one open it will make your browser very busy and can interfere with viewing other ants (or other web pages). 

# Turnites

Turnites - Click to view

Another generalization could be to allow the rulesets themselves to cycle. For example, a classical "RL" Langton ant could, on alternate steps, act like a reversed "LR" ant. This is known as a Turnite, and can produce some even more interesting results.

Although the other ants can be viewed as Turing machines in combination with the environment, these ants are in themselves complete Turing machines. That means with enough states, the ant could emulate any programmatic behavior. These ants exhibit a wide range of behaviors, as expected since they could do anything a computer could do!

The ruleset for a Turnite in this code is similar to a multi-colored 'RL' ant, but the rulesets are delimited with newlines or '/' characters. So one basic turnite might be 'RL/LR'. As coded, each turnite ruleset must be of the same length.

# Other generalizations
From here, many other generalizations could be made. We have a basic ant which defines a rule matrix, which has one rule for each state+color combination. Normally this rule will simply tell the ant to turn left or right. However, these rules could also determine the next color or state index. Or the left/right orientation change could be expanded to include things like "go straight" or "turn 45 degrees left". Many other variations are possible. Interested readers are invited to fork the open source code and explore the universe of variations.

# Quick Code Tour

The complete code used to generate the JavaScript ants and also the thumbnail pages is hosted as open source on Github. All code is under the Apache 2.0 license. It is an eclipse gwt project, but there are test cases which run non-gwt components such as a awt ant viewer and the zoo rendering utility. There are four main packages:

* awt - Utilities for outputting images and displaying ants in a pure-java context
* common - These classes define the basic mechanics of the ant programs
* gwt - Contains the gwt components to display ants. Display can be driven from html for pauseable full-window ants, or as a javascript call to launch ant dialogs, as can be seen in the ant zoos.
* zoo - These classes generate a series of ants and render them each to an image after some number of steps. Additional logic is provided to remove duplicate and uninteresting ants. The output is an html page which links to the compiled gwt script to produce the embedded pages you can see on this post.

Enjoy exploring these fascinating little creatures!


