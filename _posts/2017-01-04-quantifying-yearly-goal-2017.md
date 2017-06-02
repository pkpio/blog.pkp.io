---
layout: post
title : Quantifying yearly fitness goal
categories : [Tech, Personal]
---
I was deeply convinced that regular progress tracking is a crucial step towards achieving my fitness goal for 2017. So, I created a  simple tool which extracts my runs from Fitbit data and the final results looks like this. All y-units are in Kilometres.

<center><iframe height='940px' width='800px' frameborder='0' allowtransparency='true' scrolling='no' src='https://fitgoal.herokuapp.com/graphs/praveen'></iframe></center>

Basically it retrieves all Fitbit activities logged on or after 1st January 2017 and filters only "Run" and "Bike" activities - the goal is to cover 1000 Kilometres over the year.

If you would like to generate a graph for yourself, [create an account](https://fitgoal.herokuapp.com) and your graph will be available at https://fitgoal.herokuapp.com/user/{username}. If you don't have to own a Fitbit tracker, just the Fitbit App will do! 
 
[github-repo]: https://github.com/praveendath92/fitbit-yearly-distance
