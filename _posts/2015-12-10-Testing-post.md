---
layout: post
title: A sample post to do some blog testing
categories: [Web, Android]
---

Yet another time, I'm starting a new blog. This time it's using jekyll but not in the usual way it is supposed to be used.


What changed?
---------
- It's all json output after a ```jekyll build```
- The idea is to use these json outputs in AngularJs
- Integrate it uniformly into the existing website
- The whole setup is actually a tidious task :/

Github markdown test
=======

Code highlighing
-----

``` ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

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

Text edits
------
Auto linking : https://pkp.io

~~Strike through~~
Superscript : 2^2
_underline_
==Highlight==

