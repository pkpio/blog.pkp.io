---
layout: post
title : Syncing all Fitbit data to Google Fit
categories : [Tech]
---

I love Fitbit trackers. They promise to do just one thing - quantifying self, and they live up to it! Just like most people, I tracked my lifelogs using mobile apps before Fitbit came along. More specifically, I'm talking about Google Fit - an open ecosystem for fitness data. When I finally moved to a dedicated tracking device, Fitbit Flex at first and then to Charge HR, I noticed that there is no way to sync Fitbit data with Google Fit or any other third-party services. While Fitbit itself has a nice ecosystem of tools, graphs, badges and a social component, the fact that I cannot move "my data" around bothers me - I guess I was hoping for Fitbit to be more of a "hardware" company and let users export their data to third-party apps. In all fairness, Fitbit has an API to read all data for an account so, in theory we can build tool to automate the process. Well, it's a theory no more!

It was a lazy Sunday evening when I decided to hack a simple tool to sync all my Fitbit data to Google Fit. Surprisingly, there aren't any alternatives to do this. For example, [fitnesssyncer.com](https://www.fitnesssyncer.com/) promises to sync steps but aligns all steps for a day at 12:00 AM. Also, there's much more data in a Fitbit account. I was hoping to do this as quick as possible but unfortunately (or not), there isn't much community interest - stackoverflow questions, on Google Fit REST APIs. It quickly became clear that I cannot take any shortcuts here - for there are none, so I started going through complete Developer docs for Google Fit and Fitbit. Luckily enough, I came across [fitsync](https://github.com/tantalor/fitsync) for syncing Fitbit weight logs to Google Fit. I took this as a seed and worked my way up to adding all other data types. Checkout the [Github repo](https://github.com/praveendath92/fitbit-googlefit) for list of all supported features and setup instructions. Here is preview of the final output after a sync.

<img src="{{ site.url }}/assets/fitbit_steps.png" alt="Fitbit steps" style="max-width:100%;"/>

<img src="{{ site.url }}/assets/googlefit_steps.png" alt="Google Fit steps" style="max-width:100%;"/>


Since the sync uses better granularity for data, we get precise step count for each minute/hour. For those of you on Windows and not so command line savvy, here's a video demo of the setup process on Windows.

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/h-hhZwigyXs" frameborder="0" allowfullscreen></iframe></center>

