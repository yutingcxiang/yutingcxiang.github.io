---
layout: post
title:      "Progress Tracker - Sinatra Project"
date:       2018-08-31 13:39:16 +0000
permalink:  progress_tracker_-_sinatra_project
---


For this project, I decided to go with something more personal. I decided to create a progress tracker for my learn.co curriculum. If you're thinking we already have progress tracking for our learning, you're right and it looks something like this:

![](https://imgur.com/a/gOvAEk0)

As fantastic as this is, unfortunately, it does not help me answer my career coach's question during every meeting: how many hours did you get in? (I have a google sheet for that.)

Then the Sinatra Portfolio Project asked me to create a "custom app that is created to track something important to you."  What about a better way to track my hours?

**The Process**

As always, the most difficult part was figuring out how to get started, as in how to setup the environment and app folders that always came conveniently packaged for us in our labs. Luckily, I stumbled across the corneal gem, which is essentially a sinatra skeleton created by another student specifically for these situations (definitely check it out at https://github.com/thebrianemory/corneal). 

With the structure out of the way, I was able to layout general structure of the app. The interface would allow a student to create an account to track their study sessions. Study sessions are described by their date, how many hours were worked, and a small summary of what you studied during that time. The layout of my app was most similar to the Fwitter lab came previously so much of my structure was designed with that layout in mind.

**Issues**

The biggest headache for this project was caused by my silly naming convention. I inconveniently decided to name one of my models "Study_session", which led to many cases of Sinatra flat-out refusing to acknowledge the constant (uninitialized constant errors are real fun). After much debugging, it was simpler to just name it "StudySession" instead of looking for a fancy workaround. Definitely a lesson to be learned here about following naming conventions and paying attention to the order of my methods.


**The Result**

Overall, I'm quite pleased with the overall app. There is definitely room for improvement in the layout and structure (have yet to incorporate CSS) as well as additional functionality (a total hours tally would be useful). But after 15 hours of work (all accounted for), I was able to setup a decent site that I wouldn't mind using on a daily basis and that is a success!

![](https://imgur.com/a/P40eeuWhttp://)



