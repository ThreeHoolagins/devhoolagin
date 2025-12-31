+++
date = '2025-09-04T16:00:00-06:00'
title = 'Tinkerings 1: Riot API Utility Pipeline'
draft = false
+++

Welcome reader! This is my second post and its a recap of a previous code exploration I began way back in January of 2024, and took a couple iterations to actually complete. This is my first full-size function personal project, and something that has spun off a lot more work in my personal project area.

# The Pitch
You and your friends play League of Legends, an online MOBA,  and you've been experimenting with playing ranked recently. Coincidentally you also want something to put on your resume. Why not post everyone's rank in order in your personal league discord server? 

Here in which lies the challenge, on a regular basis, get everyone's ranks, and display them somewhere everyone participating can view. Easy, right?

# Timeline
Dear reader, if this bores you, do feel free to skip. This is a long section.

Checking [my github](www.github.com/ThreeHoolagins) history, my first attempt for this project was set on January 17th, 2024. Fhew. When first attempting this project I had finished a pretty major set of projects at work, re-writing the old angular employee time-off page into our new fancy typescript react repo. I believed at the time that I would create typescript files for all the DTOs I needed, and then build what I needed after I had all the types from the [Riot Developer API](developer.riotgames.com). This reader, was a **mistake**. If this is not known to you yet, dearest reader, while working on personal projects, especially when you have a very short history with that type of project is bad. Starting with the most tedious approach that doesn't even have a line of sight as to how it will be completed is like building a car by first crafting your spoiler. ([See attempt](https://github.com/ThreeHoolagins/rankedRaceBot))

Let's take a quick look at how I had thought this project was going to go at the time. My first thought around this was an airflow DAG, as I had worked with apache airflow for a short stint of about a year when I was with Sift, and though it had been a minute, I figured I could just “make it work” on typescript so all my types would  be nice and I'd just figure out how to run it later. 

This approach was quickly abandoned after one night of work.

To sidetrack again, I had not fully read the Riot API docs, and thought I was going to have to grab all of a player's games, see the loss/gain in LP of each one, and calculate a player's rank and LP from there. This was wrong, and significantly more complicated than I would need.

Getting back to the timeline, after 3 months I tried again. I had decided to host a website that everyone could see and immediately ran into CORS. I despise CORS with a rath reserved for mortal enemies. If you don’t know what CORS is, you’re lucky. Or maybe you just haven’t seen [Theo’s CORS video](https://youtu.be/Hifll_y8-HE?si=z9hu37iBy4VHOvy_). I won’t judge (let him know I sent you). To address the CORS issue, I had set up an express server to work as a middlelayer and let’s just say this repo also only has commits from one day. ([See attempt](https://github.com/ThreeHoolagins/lolRankedRaceServer))

This was also abandoned after one night. Fast-forward I made a couple small websites and projects that get finished, my pyBoxCoach which was too simple to be useful, but cool nonetheless, my [get-this-man-a-hat](https://threehoolagins.github.io/get-this-man-a-hat) site which was a dorky one night project, and my [lol-team-jerseys](https://threehoolagins.github.io/lol-team-jerseys/) site. The last of which was my first complete project with the Riot api, more specifically Data Dragon. One more attempt making it in bun, and we reach the summit of this project.

# Fuck it, I'm using python, and it’s gonna work

When approaching this again in January of 2025 I had some new motivators. The new 2025 ranked season was starting, and it seemed we may actually be more on top of playing together, and I'd attempted this project 3 times already. It was this time I decided I needed to make progress first, make it good second.

I choose python because python is easy to use/learn, and because I could just run it on my computer. I made a full working program, with a lot of assumptions, and a simple structure. A runner file, to take care of doing all the annoying pieces of taking console input and formatting that properly, and a separate file for doing the actual work. 

![A diagram displaying the above statement for simplicity](/devhoolagin/runnerDiagram.png)

This was the extent of my abstraction. There were a couple methods to handle annoying things, and since this was going to run as a job, instead of trying to handle the rate limiting smartly, I just added a delay between calls that would ensure I never hit the rate limit. After all, this is not a latency sensitive project, as it just needs to run once a day.

For this, I just used the python requests standard library, and actually got it from riot api to discord.

![Picture of the first ranked race bot post on discord, with Shock as the only placed one.](/devhoolagin/rankedRaceBotFirstPost.png)

Tada! To go into how this worked abstractly, check below.

![Diagram depicting original messageGroup process](/devhoolagin/rankedMessageDiagram.png)

How did I run this to post daily you might ask? What webserver? What AWS, Vercel, GCP config? Well, the answer is simpler than you may think. I have a windows desktop I rarely turn off, and I simply scheduled a windows task to post every Tuesday, Thursday, and Saturday in the morning to keep the heat up! +1 for using your already available tools.

# Itterate, Itterate, Itterate.

After actually having this and getting to have the cool of it posting consistently, I realized I had more additions I wanted, so I abstracted my player object so it could handle more of the logic a week later, and after it being on for 4 months I added better message display, made it store a file for what was posted last time, so it simply wouldn't post if it's the same as last time, and adjusted my windows task to run every day.

This was when the project was finally in a really cool spot. I had a program, which was useful to me and my friends, messaging every couple of days as we competed in our race to be at the top rank, and the project was simple enough to debug and sturdy enough to work. You have no idea how cool this is until you’ve taken something from an idea into part of your day-to-day life. 

After, I added better logging, started making it send me failed logs to my email on pipeline crash, and cleaned up my code with riot api getting nicer to use in July. I added a job to post league patches within a day of them being announced, with links and the summary image to our discord server, and I've lastly started making it keep track of skinlines and updating on new patches to hopefully use for a new version of the lol-jerseys website, as the time-to-functional of that website is astronomically bad. [See repo here!](https://github.com/ThreeHoolagins/weekly-ranked-lol-shoutout)

# A Janky Aside

As part of embracing the janky-ness of personal projects and rolling with it, the way I get the image link to post for new patches is, frankly, atrocious. And I love it.

First, we check our file for the last patch that we successfully found. This file needs to exist for this job, as we need a starting point. Then, we take that, and try to hit a blog post that may or may not exist at `leagueoflegends.com/en-us/news/game-updates/patch-25-{current subpatch}-notes`. As you may know, this is bad because we assume that this structure for riot's uri stays consistent. This would mean they never change how things are hosted, how they wanna lay out their website, assuming they never move this to a patch notes website or subdomain separate from the site, this is a faulty assumption, but one that has historically (since May of 2025) worked. After doing this, we use the patch in the following code segment.

```
def get_current_patch_image_uri(patch_version):
    r = requests.get(get_patch_notes_url(patch_version))
    if (r.status_code != 200):
        raise PatchNotPostedException
    soup = BeautifulSoup(r.content, "html.parser")
    links = soup.find_all("a", class_="skins cboxElement")
    for link in links:
        return link.get("href")
```

Dear reader, it may not be immediately obvious, but we use a web emulator, BeautifulSoup to parse the html, looking for all anchor tags using the class "skins cboxElement" and simply get the first one's link reference. This assumes they never change frameworks, article formats, naming conventions for their css, never rewrite, never refactor. This has worked since May of 2025, and highlights the magic of these kinds of personal projects. No money is on the line here, and if it grabs the wrong image, or breaks, I can check the logs that night, find out what's wrong, and patch it. Good as new.

# Conclusion

Build thrown together projects! I learned a lot about completing personal projects with this, and to date I have >75 successful posts. Some things I'd like to do to make the project even better.

1. Dockerize the project:
Currently this project has a lot of windows based assumptions, and I'd like to change that, and maybe start running it on my raspberry pi so my poor pc can take a break here and there.
2. Get it setup for newbies:
Right now I have a data file that you could figure out but would be painful to setup. I'd like to get this setup so that someone can plug and play the values needed for their friends, their discord server, and their bot and use it themselves for their own personal ranked race. This goes hand in hand with number 1.
3. Get more input:
This has been done for me and my friends, but right now, I'd love to make it nicer for more people.

Thank you for reading. If you like this and want to see more, or would just like comments enabled, let me know at cbcunningham20@gmail.com, or just text me if you know me :)

