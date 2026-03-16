+++
date = '2026-03-15T22:38:37-06:00'
draft = true
title = 'Vibecodeventures 1'
+++
I’m starting this new series for making stuff on a short timeline. I wanna say the title to this is mostly joke, but here’s the background.

Background to Vibecoding
My workplace checkr is increasing its encouragement of use of ai tools and at this point I feel a need to start picking this stuff up. And, thanks to work I’ve experienced using lovable for ui, and have previously used ChatGPT for planning out a person project I later abandoned.

Background to THIS project
So I’ve picked up self hosting, as mentioned in this article, I’ve been setting up a new campaign in foundryvtt, and with that adding music. For purposes of this article, I am only installing royalty free music from YouTube, but these modules that allow you to do that easily have been hunted down. So I had an idea, what if I had Claude make it? It’s supposedly a really simple solution, take a link, download the Audio, and add it to foundry. Simple, right?

Double check your homework
So in making this I prompted Claude, and got back a weirdly complex solution. Run an express server, have most stuff live on the client side, install a cli tool, and honestly felt way too complicated and I didn’t want to worry about all that. So I told it to remake it to live on the server. This was the problem.

Pic of output

It hallucinated an entire way of doing server side modules that didn’t exist. I did find out, but only after debugging why the upload button didn’t work. So, with the hints of a possible solution I got from the first one, and again not wanting to run a second dedicated server just to downloading YouTube videos, I asked it to make me a really simple Linux command! See below!

Really simple, but pretty effective, and now I don’t haft to download to my pc through a sketchy site and upload from my computer taking forever to get anything on there.

Future ideas
One thing I learned from work is that UI’s are very easy to get something decent out, so for next vibecodeventure I am going to make an internally hosted habit tracker. We’ll see how it goes.

-Hool

P.S. if this feels like a pivot from my previous ai assertions, it kinda is. Idk what else to say about it other than using it at work has shown me how nice it can be, and more importantly, the reduction in cognitive load for personal projects I feel will get me creating more. We’ll see!
