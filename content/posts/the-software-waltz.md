+++
date = '2026-01-16T12:00:00-06:00'
title = "Blog 5: The Software Waltz"
draft = false
+++

Hi Reader! I wanted to take some time today to talk about an idea I’ve been having in my head ever since I got more senior at Paycom.

## Background

Software is an engineering discipline that is often at odds with the business side of itself. Unlike in oil and gas or civil engineering situations, where making something 2x or 3x safer than what you need is an engineering norm, software often launches half baked. The design is often good enough to get the product out and with growing systems for software specifically (Agile, Kanban) versus old engineering norms (Waterfall) we often even abandon the idea of an end state.

As previously state, this makes an environment where business needs (shipped as fast as possible making $$$) come into conflict with engineering needs (extensibility, quality system design, automated testing). Good business leaders in software are often ones in which understand this trade off and act accordingly, but often there are business leaders less adept to this, and to make a controversial statement to engineers, business leaders shouldn’t haft to know software that well. They should know the business, it's constraints and timelines (when you run out of money), product should know how the product works(calculator adds numbers, stores memory of previous operations), but neither group should haft to have an understanding of software(which database, performance tradeoff, etc). 

That's *your* job, and your job to translate to them.

## Seniors Engineers, More than architects

![Frieren Gif](https://media1.tenor.com/m/qO4_SbfQMkgAAAAC/drinking-tea.gif)

I think often software is depicted and discussed as ruled by the smartest (and most smartass), where technical prowess beats all other traits, and that technical skills are the ONLY important thing. I would hope we are beyond that now, it's not the 90s anymore, being a nerd is cool, and the longer you progress in a company the more you’ll realize that having finesse with business people will be one of the most valuable skills of your entire career. I believe this to be one of the most defining features of a great senior engineer, and a skill I want to ensure I grow in every company I’m at.

Senior Engineers are often talked about as simply advanced nerds, highly skilled coders, smarter versions of junior engineers. The thing you realize with more time though, is that the soft skills of a senior engineer make miles more difference than advanced education on the latest framework/design pattern/languages. The most obvious of these skills is mentoring and teaching junior engineers in a time effective manor, and in a way that teaches them how to interact with seniors. To be frank, junior engineers are often <ins>just</ins> college students, and the induction into the workforce is a harsh transition for many college students. They are often racked with questions like:

> I am asking too many questions? How much do I look into an issue before reaching out? What are good questions to ask, and when are good times to ask them? 

A skilled senior engineer will give them suggestions, schedule time to pair, and set expectations as to when a junior can expect to hear back from them(EOD, pair tomorrow morning after standup, etc). When left to their own devices, junior engineers will learn this eventually, but without a senior engineer giving them clear guidelines, these skills can take years. With a very soft skilled senior, in a few months a junior engineer can be asking questions and respecting time like a mid-level engineer.

## The most valuable senior engineer trait

It is my believe the most important skill to hone as a senior engineer is product negotiations, and weaving in your technical desires into this. This taps into all the technical skills a senior is generally expected to have, and weaves in the business know how. We can ship x in 16 weeks, or if you need it in 12 we can cut down to y features, to be production ready we’ll need z more weeks. Working with your leader or EM on this frees them up to worry about budget or leadership meetings and produces so much value for businesses.

In addition, working on scaling the systems is also more of a team concern. Your engineering org SHOULD care about this, but not everyone gets the pleasure of being at a company that cares what the org says about this type of stuff before it breaks.

I think engineers are often resistant to this type of talk. I think they often view themselves are developers working on making the best system they can, antagonized by the business telling them what they can do and making the whole process harder on them.

![Frieren Gif](https://media1.tenor.com/m/ve_GpM7QEIYAAAAd/stark-fern.gif)

> Life reenactment of engineers being told by business leaders they can’t refactor the entire codebase again

## The Software Waltz

So now, 500+ words later, my idea. I think for updating old systems (which theoretically, is all the time in software) we should work to weave it in with our new feature development. Wanting to move your team’s business logic to a new micro service? Your first reaction might be to ask business leaders for time to do a migration, but this can be fraught with issues, and if you’re lucky enough to get this opportunity it may be valuable, but often business sees no value in it. So, waltz! Give them what they want, move in their northward direction, but move east some with it at well. Put the new feature in the new micro service. Gotta update the preexisting business logic because it’s too slow and needs re-written? Move it to the new service!

It’s my belief that your team should be on the lookout for good opportunities to weave in system goals into your business needs in a way that might delay them a week or two more than normal, but are not very visible to the business. And more importantly than that, your team should be on the same page of the direction your looking to move in, and senior should be keeping an eye on when and where we can align our goals with new features.

As an engineering team, you are dancing with the business side of the company, keeping in time as they need, and drifting yourself towards where you want to be technically. (Small Frieren spoiler below)

![Gif](https://media1.tenor.com/m/KlihBLr2xRQAAAAd/sousou-no-frieren-frieren-beyond-journey%27s-end.gif)

## Giving an example

When I was working at Paycom, there was not a strong unit testing culture in my team. Often things just needed to get out, and business teams put a lot of pressure on the developers to get things done on short timelines. When I was working on a project that was moving our .net framework code into .net core and a newer c# version, I used that time to revisit the old unit tests, and get all 1000+ of them running again, in the new version. 

This was not listed out by product, and the framework update was to enable containerization for the business, but I made sure to weave that into my breakdown of the project, which only added a little more time, but enabled devs to simply "run all tests" in a way that had not been possible for years. Automated testing was not setup in the pipeline, but alas, you can only wish for so much change at any one given time. 

I also used this opportunity to setup a tech talk on our testing frameworks for this micro service and how to setup tests, adding documentation, and helping other developers write their first tests. We *all* leveled up as engineers, and had I not payed attention and decided to dance with the business constraints in the direction I wanted our engineering practices to go, none of these secondary effects would have happened.

## Conclusion
Soft skills in my experience have been some of the least valued or poorly discussed topics I see in software. In business contexts, public service, or nonprofit work. An attitude of flexibility in the engineering teams trailblazed by seniors I believe to be essential. All things made must be a compromise of the best version and the resources and buy in available.

\-  Hoolagin

*P.S.* Super excited for the second season of frieren! Gotta convince my partner to finish the first season, but the first season has been beloved to me, hence the gifs. I hope they were fun!