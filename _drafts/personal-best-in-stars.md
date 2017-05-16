I just received my first 100+ stars for one of my personal projects, [fitbit-googlefit](https://github.com/praveendath92/fitbit-googlefit), on Github. This gave me a good reason to talk a little bit about how it got there. Before we begin, here are the latest numbers:

<center>
<iframe src="https://ghbtns.com/github-btn.html?user=praveendath92&repo=fitbit-googlefit&type=star&count=true" frameborder="0" scrolling="0" width="170px" height="20px"></iframe>
<iframe src="https://ghbtns.com/github-btn.html?user=praveendath92&repo=fitbit-googlefit&type=fork&count=true" frameborder="0" scrolling="0" width="170px" height="20px"></iframe>
<iframe src="https://ghbtns.com/github-btn.html?user=praveendath92&repo=fitbit-googlefit&type=watch&count=true&v=2" frameborder="0" scrolling="0" width="170px" height="20px"></iframe>
</center>

It all started on an insomniac night when I was aimlessly surfing - "Look around casually and randomly, without seeking anything in particular”, the internet. I have been using Fitbit for about 2 years then and they have very few 3rd party integrations and heavily rate-limited APIs (150 requests per hour per user). Google Fit promised a more open platform and also, higher limits for API calls (3600 requests per hour per user). However, given the popularity of Fitbit trackers, I was confident I could find a good integration tool to migrate all (or at least some) of my data to Google Fit. Surprisingly, there was no such tool so, I figured I will just write one - how hard can it be? - just a couple of nights tops.

And thus the tool was born. I was kind of sure this could gain popularity (or at least, would beat my then personal best in stars) since a similar tool which offered only weight data sync had already gotten 50+ stars. Luckily for me, I had just read this post about [getting people to notice your Github repo](https://medium.freecodecamp.com/getting-others-to-notice-your-github-repository-697f24539455). I took pointers from there and made a nice `Readme` file with "fancy" gifs about how it looks in action and screenshots of the final output. My approach actually involved a lot more steps than other one-click sync websites but I knew mine had much better precision - for the record, their precision was per day and mine was per second! So, I highlighted this at the very onset in my `Readme` - after all that was my selling point and the major reason for me to create this. 

Then, I added the following non-intrusive request to users at the end of a successful run. 

```
--------------------------------------------------------------------------
                                     Like it ?                            
star the repository : https://github.com/praveendath92/fitbit-googlefit
--------------------------------------------------------------------------
```
Posted about the tool on XDA and other places where people already requested for this. Answered any queries from users promptly and even went on to make a Youtube video to demonstrate the setup for Windows users. Overall, it was more work than what I had initially expected but as the star count kept raising, it kept me motivated to keep the support going and fixing any bugs reported through issues. 

Obviously, all this has no tangible impact on me - monetary or otherwise, but in my opinion, having a popular repository earns some kind respect for developer and positive first opinion about their skill. The lack of it, however, doesn’t imply the contrary.