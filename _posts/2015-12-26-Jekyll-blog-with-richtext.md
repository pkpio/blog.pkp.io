---
layout: post
title: A jekyll blog with rich text support
categories: [Tech]
---

Tl;dr : This is show down of the rich text features supported by the [Jekyll][jekyll] blog setup as you see right now.
To get more information on the actual setup, read the previous post.

Titles and subtitles
==============
Supports various levels of titles

Smaller title
-------


Code highlighting
=====
Language specific code highlighting

```java
/******************************************************************************
 *  Compilation:  javac HelloWorld.java
 *  Execution:    java HelloWorld
 *
 *  Prints "Hello, World". By tradition, this is everyone's first program.
 *
 *  % java HelloWorld
 *  Hello, World
 *
 *  These 17 lines of text are comments. They are not part of the program;
 *  they serve to remind us about its properties. The first two lines tell
 *  us what to type to compile and test the program. The next line describes
 *  the purpose of the program. The next few lines give a sample execution
 *  of the program and the resulting output. We will always include such 
 *  lines in our programs and encourage you to do the same.
 *
 ******************************************************************************/

public class HelloWorld {

    public static void main(String[] args) {
        // Prints "Hello, World" to the terminal window.
        System.out.println("Hello, World");
    }

}
```

Auto linking of urls
========
This was a simple text link : https://pkp.io

Ordered lists
======
 1. One
 2. Two
    1. Two dot one
    2. Two dot two
 3. Three
 
Unordered lists
=======
 - Item one
 - Item two
    - Sub item one
    - Sub item two
 - Item three


Rich text features
=========

 - Applying ~~Striki through~~ parts of texts
 - Superscript notation : 222^232
 - And _underline_ some text
 - Even nice ==Highlighting== some of it
 

FontAwesomeIcons
=========
FontAwesome icons such as {% icon fa-heart %} and spinner like {% icon fa-refresh fa-spin %}


[jekyll]: https://jekyllrb.com/
