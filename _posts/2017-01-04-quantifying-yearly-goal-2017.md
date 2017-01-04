---
layout: post
title : Quantifying yearly fitness goal
categories : [Goals, Fitness, Hack]
---
I was deeply convinced that regular progress tracking is a crucial step towards achieving my fitness goal for 2017. So, I created a  simple tool which extracts my runs from Fitbit data and the final results looks like this. All y-units are in Kilometres.

<center><iframe height='300px' width='600px' frameborder='0' allowtransparency='true' scrolling='no' src='http://fitgoal.pkp.io' ></iframe></center>

Basically it retrieves all Fitbit activities logged after 1st January 2017 and filters only "Run" activities - since the goal is to cover 1000 Kilometres over the year in running. The tool exports the cumulative distance for each day since January 1st in ```distance.json``` file. The web application uses data from this file to build a graph as shown above. For more details, check out the [Github repo][github-repo].

 
[github-repo]: https://github.com/praveendath92/fitbit-yearly-distance
