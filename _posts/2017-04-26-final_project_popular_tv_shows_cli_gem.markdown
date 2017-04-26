---
layout: post
title:  "Final Project: Popular TV Shows CLI Gem"
date:   2017-04-26 01:18:54 -0400
---


As a TV lover, this project was a great opportunity to try to bridge my two passions: coding and television. As someone who watches a lot of TV, it can be hard to find the next great show to watch. On the other hand, there are a lot of options out there, so someone in the market for a new TV show may not know what to watch next. This sparked my idea for a CLI gem:

Popular TV Shows!

TV Guide has a great list of the [Most Popular TV Shows](http://www.tvguide.com/tvshows/) on television/streaming services. With 49 options, and specific TV show profiles, this was the perfect website to scrape.

I started my journey by watching a [CLI GEM Walkthrough](https://www.youtube.com/watch?v=_lDExWIhYKI), by Avi, to help me get started. Definitely recommend since you may think you know what you're doing, but without the safety net of pre-built labs with tests, coming up with your own project from scratch can be daunting.

After getting started from the video, I was ready to begin scraping. And this is where my first mistake happened. With 49 options for television shows, and a premliminary check through the first few TV shows in the list, I figured every page would be the same, so I coded my scraping tool. 

Boy, was I wrong. As it turns out, not every page is the same. Don't freak out or feel sorry for me. Luckily, the changes between a few of the TV Show profile pages were small so after I stopped freaking out for no reason (am I the only one who does this?), I realized just adding in a few verification checks and slapping in "N/A"'s easily fixed my issue.

My next issue, was being able to print with multiple colums. 49 items in a list is a lonnnnngggg list...and not so pretty. So, after googling around, installing random people's gem's, I found a way to do it and got this:

![](http://i.imgur.com/Ne0XxYW.png)

The last issue, which I still need to fix, but will definitely need some help with, is how to optimize my code so that it runs faster. Waiting for the list to populate takes wayyyyyy to long. 

I'm hoping that I can add this as an actual gem because I think it's a pretty neat idea.

