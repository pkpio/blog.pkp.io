---
layout: post
title: Building a responsive personal website from scratch
categories: [Web, Angular]
---

I started to feel quite blasé about the site I use to market myself! It was already 2 years old and that's a long time, especially in tech, to regard something as old and probably obsolete - in comparision to the prevailing! Frankly it's about time that I start catching up with what's {% icon fa-fire %} in Web!

No to pre-built templates
============
So, I set to create a new website for myself, again! The tech landscape has changed a lot in the last 2 years - especially the attention given to Mobile first or responsive design. I didn't want to use a pre-built template that I could buy for a few bucks. Part of my online persuasion stems also from the fact that what you see is what I made. A from scratch development gives me immense flexibility in terms of design, architectural choices and a sense of satisfaction.

Ground rules
============
Unlike the times before this, I decided to set some ground rules before I set my course to coding. These include architectural choice and a few more guidelines : 

 - Responsive layout
 - Simple and clean UI
 - Consistency in Design and Code
 - Proper dependency management
 - UI and Data isolation

Techonolgy choices
============
After examining a few popular choices, I arrived at the list below:

 - [AngularJS][angular]
 - [Bower][bower]
 - Angular plugins
   - [Material][ang-md]
   - [Timeline][ang-tl]
   - [Route][ang-route]
   - [Discuss][discuss]
   - Typewriter
 - [FontAwesome][fa]
 - [Jekyll][jekyll]

Building 
============
[AngularJS][angular] is freaking awesome! - I'm in {% icon fa-heart %}. Using [Angular material][ang-md] I quickly arrived at a basic template for the website with just one dynamic element - the only changing component of the website - consistency and uniformity, remember? 

Once I have a basic template for the site, I just had to make templates for each page - templates because I wanted to maintain isolation between page design and the actual data. Keeping other ground rules in mind, I arrived at below structure for the app.

```
root
  |- data                      // User data for each page
  |   |- about.json
  |   |- academics.json
  |   |- intro.json
  |   |- project.json
  |   |- work.json
  |
  |- extra                     // Config and setup files that come in handy on fresh setup
  |   |- apache.conf
  |   |- apache_mods.sh
  |
  |- img                       // Image files
  |   |- projects
  |   |- work
  |
  |- js                        // Javascript files. Each file has controller for a page 
  |   |- libs
  |   |- about.js
  |   |- academics.js
  |   |- app.js
  |   |- blog.js
  |   |- intro.js
  |   |- post.js
  |   |- project.js
  |   |- work.js
  |
  |- style                     // CSS styles 
  |   |- angular-typewrite.css
  |   |- markdown.css          // for markdown - html convertor in blog
  |   |- main.css
  |
  |- view                      // Page templates
  |   |- 404.html
  |   |- about.html
  |   |- academics.html
  |   |- blog.html
  |   |- intro.html
  |   |- loading.html          // 3 cogs showed at async loading
  |   |- post.html
  |   |- project.html
  |   |- work.html 
  |
  |- index.html                 // Main template and landing file for all pages
  |- .htaccess
  |- bower.json                 // Bower depedencies. Install these first!
```

So far so good. Then I also wanted to have a blog to go along. Install wordpress, right? - I wish it were that simple. Anyway, more on blog setup later.

Blog setup
============
Rules first! A big no to wordpress - I want to be in full control of my blog and it's content. So, my obvious choice would be [Jekyll][jekyll] - a blog aware static site generator. But then I'm also looking for a uniform and consistent integration of this with the exisiting site. So, I would prefer a blog with a simple JSON API, because I'm already using JSON for user data, but not go so far as a full wordpress setup - that would have been easy though! 

Luckily, jekyll is very open! I created templates with JSON structure and HTML output embedded in the JSON. Obviously, there was more to it! Here are some additional tweaks, using jekyll plugins, I did to get a blog that supports rich text content :

 - Redcarpet Markdown-HTML convertor
 - Category indexes plugin
 - Language specific code blocking
 - FontAwesome Icons
 - A few other plugins in Redcarpet itself

You may check the [blog source code][blog-src] for more info on this.


Add-ons
============
We all love addons! Since everything so far is working great, I decided to throw in a couple of add-ons :

 1. Discuss plugin:
    Because a blog with no place to voice your opinion {% icon fa-comments-o %} would be dull!

 2. Crawler friendly version:
    As great as AngularJS is, it fails miserably when it comes to dealing with web crawlers! Thanks to [Prerender.io][prerender], that's a solved problem now! You can check this setup in the ```.htaccess``` file

[angular]: https://angularjs.org/
[ang-md]: https://material.angularjs.org/
[bower]: http://bower.io/
[ang-tl]: https://github.com/rpocklin/angular-timeline
[ang-route]: https://docs.angularjs.org/api/ngRoute/service/$route
[discuss]: https://github.com/michaelbromley/angularUtils/tree/master/src/directives/disqus
[fa]: https://fortawesome.github.io/Font-Awesome/
[jekyll]: https://jekyllrb.com/
[blog-src]: https://github.com/praveendath92/blog.pkp.io
[prerender]: https://prerender.io/
