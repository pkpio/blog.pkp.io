---
layout: post
title: Building a responsive personal website from scratch
categories: [Web, Angular, Material]
---

I arrived, yet again, at those points of time when the usual bores me. I'm not talking about some adventurous outdoor activity, just the website I have been using to market myself for over 2 years now! That's a long time, especially in tech to consider something as old or probably obsolete - at least in comparision to the prevailing trends!

# No to pre-built templates
So, obviously, I set to create a new website for myself, again! The tech landscape has changed a lot in the last 2 years - especially the attention given to Mobile first or responsive design. I didn't want to use a template that I could buy for a few bucks - part of selling myself stems also from self designed and developed website. A from scratch code gives me immense flexibility in terms of design, architectural choices and a feeling of great satisfaction.

# Ground rules
I must lay some ground rules before I set my course to coding. These include my final goals, structural choices and consistency. Here are some of them:

 - Responsive
 - Material design
 - Uniformity and consistency
 - Proper dependency management
 - Simple and clean
 - Okay to use plugins
 - Design and data isolation

# Techonolgy choices
After examining some currently popular technologies I arrived at the list below:

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

# Building 
[AngularJS][angular] in freaking awesome! Using [Angular material][ang-md] I quickly arrived at a basic template for the website with one dynamic content element - this is the only changing component of the website - consistency and uniformity, remember? 

Once I have a basic template for the site, I just had to make templates for each page - templates because I wanted to maintain isolation between page design and the actual data. Keeping other ground rules in mind, I arrived at below structure for the app.

```
root
  |- data                      // user data for each page as JSON files 
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
  |   |- about.json
  |   |- academics.json
  |   |- app.json
  |   |- blog.json
  |   |- intro.json
  |   |- post.json
  |   |- project.json
  |   |- work.json 
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

[angular]: https://angularjs.org/
[ang-md]: https://material.angularjs.org/
[bower]: http://bower.io/
[ang-tl]: https://github.com/rpocklin/angular-timeline
[ang-route]: https://docs.angularjs.org/api/ngRoute/service/$route
[discuss]: https://github.com/michaelbromley/angularUtils/tree/master/src/directives/disqus
[fa]: https://fortawesome.github.io/Font-Awesome/
[jekyll]: https://jekyllrb.com/
