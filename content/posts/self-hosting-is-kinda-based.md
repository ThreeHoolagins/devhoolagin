+++
date = '2026-02-11T12:00:00-06:00'
title = "Tinkerings 3: Self Hosting is Kinda Based"
draft = false
+++

Okay so I gotta clarify something real quick- I do not like how people on youtube talk about self hosting. In my opinion, self hosting is a pain in the ass and NOT a realistic replacement for the average person to learn. Hell, my interest is explicitly because setting up services with docker and the such is a valuable skill in my industry.

That being said, I have been setting up my headless raspberry pi since my last article, and I wanted to talk about what I’ve been looking to setup on my pi!

# Ranked Race
Shoutout to my first tinkerings article, ["Tinkerings 2: How to Hate Your Pi"](/posts/how-to-hate-your-pi), where I talked about this for the first time. Along with this python project I made a discord bot with a command to calculate your ranked winrate. This is still a little messy, and not with a db and other quality of life items, which i will fix at some point but eh.

This is currently being run by setting up a screen session and a virtual enviroment. 
```bash
screen
# Some loading done
python -m venv myenv
source /myenv/bin/activate
```

But for those of you familiar with the repo:

```bash
pip install -r requirements.txt
python commandsBot.py
```
Then followed by Ctrl+A and Ctrl+D to detach from the screen session. This is so that it can be allowed to run after ive exited my ssh session, which is how I’m connecting to my headless pi. If you want to find your screen sessions in the future, you can use `screen -ls`.

# FoundryVTT
I’m a long time dnd player, though I’ve been playing less as time has gone on. And as someone interested in finance, I’ve gained a growing interest in getting out of subscription hell. At time of writing, I think I’ve paid over 500$ for roll20.

When I used to watch more TTRP youtube that wasn’t Legal Kimchi, I saw a lot of stuff for FoundryVTT its its initial viralness and used it for a campaign or two but to be fair it wasn’t as comparable and self hosting was something that I really hadn’t done, and hadn’t configured anything for work yet. To get it running after downloading and doing some basic setup, I used the same screen function to detach from the process:

```bash
screen -d -m node resources/app/main.js --dataPath=/path/to/foundrydata
```

This go around, hosting basically a website on my raspberry pi, this was fire. Easy to login, easy to run. See below!

![Foundry Login Page](/devhoolagin/foundryvtt.png)

And even more based than that, the integration with 5etools via [plutonium](https://wiki.tercept.net/en/Plutonium), my favorite dnd ease of use website is bonkers good. Now, just to get things into my game I don’t have to spend 5 minutes per npc entering information, and when using non-srd classes I can just import them. And before anyone gets on me for not paying for the Roll20 modules, I’ve already bought literally all of the dnd 5e books excluding a few adventures. I just like that it makes doing things online easier. Look at this! How cool!

![Plutonium Importer](/devhoolagin/plutonium.pong)

# Conclusion
I was planning on having more things to talk about, but honestly Iv'e been busy with the job search. Things left I want to put on here include a website and a reverse proxy to make external access to my local network easier, as I finally have a domain attached to my IP. But you don't get to have that reader, remeber, bounderies!

![Frieren blowing kiss](https://media.tenor.com/EC6mBMhIRugAAAAM/frieren-beyond-journey%27s-end-sousou-no-frieren.gif)

This is a short one, but I've got so many written at this point that I need to just edit them and get them out. See you later, you aligator.

\- Hool