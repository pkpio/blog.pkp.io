---
layout: post
title : Quantifying yearly fitness goal
categories : [Goals, Fitness, Hack]
---
I was deeply convinced that regular progress tracking is a crucial step towards achieving my fitness goal for 2017. So, I created a  simple tool which extracts my runs from Fitbit data and the final results looks like this. All y-units are in Kilometres.

<center><iframe height='400px' width='800px' frameborder='0' allowtransparency='true' scrolling='no' src='http://fitgoal.pkp.io' ></iframe></center>

Basically it retrieves all Fitbit activities logged after 1st January 2017 and filters only "Run" activities - since the goal is to cover 1000 Kilometres over the year in running. The tool exports the cumulative distance for each day since January 1st in ```distance.json``` file. The web application uses data from this file to build a graph as shown above. This graph is auto-updated with latest data at the top of every hour. 

If you would like to generate a graph for yourself, check out the [Github repo][github-repo]. You don't have to own a Fitbit tracker, just the Fitbit App will do! I will be glad to help you in tuning the tool to fit your yearly goal.

 
[github-repo]: https://github.com/praveendath92/fitbit-yearly-distance
