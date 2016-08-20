---
layout: post
title : Syncing all Fitbit data to Google Fit
categories : [Hack, Tool]
---

I love Fitbit trackers. They promise to do just one thing - quantifying self, and they live up to it! Just like most people, I tracked my lifelogs using mobile apps before Fitbit came along. More specifically, I'm talking about Google Fit - an open ecosystem for fitness data. When I finally moved to a dedicated tracking device, Fitbit Flex at first and then to Charge HR, I noticed that there is no way to sync Fitbit data with Google Fit or any other third-party services. While Fitbit itself has a nice ecosystem of tools, graphs, badges and a social component, the fact that I cannot move "my data" around bothers me - I guess I was hoping for Fitbit to be more of a "hardware" company and let users export their data to third-party apps. In all fairness, Fitbit has an API to read all data for an account so, in theory we can build tool to automate the process. Well, it's theory no more!


# Introduction
-------------
It was a lazy Sunday evening when I decided to hack a simple tool to sync all my Fitbit data to Google Fit. Surprisingly, there aren't any alternatives to do this. For example, [fitnesssyncer.com](https://www.fitnesssyncer.com/) promises to sync steps but aligns all steps for a day at 12:00 AM. Also, there's much more data in a Fitbit account. I was hoping to do this as quick as possible but unfortunately (or not), there isn't much community interest - stackoverflow questions, on Google Fit REST APIs. It quickly became clear that I cannot take any shortcuts here - for there are none, so I started going through complete Developer docs for Google Fit and Fitbit. Luckily enough, I came across [fitsync](https://github.com/tantalor/fitsync) for syncing Fitbit weight logs to Google Fit. I took this as a seed and worked my way up to adding all other data types and finally ended up with the following features.


# Features
---------
- [x] Steps - minute level precision
- [x] Distance - minute level precision
- [x] Heart rate - second level precision
- [x] Weight
- [ ] Body fat (disabled temporarily)
- [x] Activities 
  - [x] Running
  - [x] Swimming
  - [x] Biking
  - [x] Volleyball
  - [x] Walking
  - [x] Badminton
  - [x] Workouts
  - [x] Fencing
  - [x] Cricket
  - [x] Football
  - [x] Hiking
  - [x] Few others -- suggestions welcome!
- [x] Calories - minute level precision
- [ ] Floors - minute level precision
- [ ] Elevation - minute level precision
- [ ] Food logs

Since the sync uses better granularity for data, we get precise step count for each minute/hour as you can see below.

<img src="{{ site.url }}/assets/fitbit_steps.png" alt="Fitbit steps" style="max-width:100%;"/>

<img src="{{ site.url }}/assets/googlefit_steps.png" alt="Google Fit steps" style="max-width:100%;"/>


# Setup
-----------
Clone the [Github repo](https://github.com/praveendath92/fitbit-googlefit) and while you are it, thrown in star to the repo ;) This setup is a one time thing so be patient for the first time. After this, regular syncs can be done without any interaction from you.

1. Install dependencies
-------------------
This is a python3 application so install all the dependencies using ```sudo pip3 install -r requirements.txt```


2. Fitbit setup
-------------------
All instructions below **must** be performed using the **same** Fitbit account you want to sync with Google Fit.

- Register a new Fitbit application on [Fitbit Developers Console](https://dev.fitbit.com/apps/new)
- Use the information below:

```
Application Name : --
Description : --
Application Website : --
Organization : --
Organization Website : --
OAuth 2.0 Application Type : **Personal**
Callback URL : http://localhost:8080/
Default Access Type : Read-Only

Note : 
1. Use your own information for fields marked --
2. Make sure you copy the Callback URL exactly (including the last /)
```
- Hit save and make a note of ```OAuth 2.0 Client ID``` and ```Client Secret```
- ```cd /auth``` and run ```python3 auth_fitbit.py <client-id> <client-secret>```
- This opens a popup in the browser. Authenticate and done!


3. Google Fit setup
-------------------
- Go to the [Google Developers Console](https://console.developers.google.com/flows/enableapi?apiid=fitness)
- Click ```Continue```. Then select ```Go to credentials``` and select ```Client ID```
- Under Application type, select ```Other``` and hit ```Create```
- Make a note of ```client ID``` and ```client secret```
- ```cd /auth``` and run ```python3 auth_google.py <client-id> <client-secret>```
- This opens a popup in the browser. Authenticate and done!


# Usage
------------
Start the sync using ```python3 app.py```
Update the ```config.ini``` with your own preferences. 

1. Get command line help using the ```-h``` flag. 
2. Arguments passed through command-line take higher priority over ```config.ini``` values.