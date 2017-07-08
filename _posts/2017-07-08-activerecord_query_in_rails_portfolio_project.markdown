---
layout: post
title:  "ActiveRecord Query In Rails Portfolio Project"
date:   2017-07-08 05:09:36 +0000
---


Keeping with the theme of my other projects and one of my major interests in life, I have created a TV show list app for my Rails Portfolio Project. The idea of this app is kind of like Netflix and Instagram had a super awesome baby of the TV app variety. Users can view a list of all popular/current TV shows (by "all", I mean 4 shows because this is a **super** **basic** web app) and can add those show to their own list, as well as create their own shows.

One of the more interesting requirements of this project is to add a scoped query of an ActiveRecord Relation. Basically, I figured it could be useful for users to see which TV show is the most popular. Having gone through a brief introduction to PUNDIT, I realized this would be the perfect gem to implement in my project.

The first step was getting Pundit into my project. Feel free to take a look at the [documentation](https://github.com/elabs/pundit), which luckily, is very simple. I added the gem to my Gemifile, updated my Application Controller to `include pundit`, and did a quick ``` rails g pundit:install ```. I created my own policy for my `Show` model...and then got stuck.

How do I query finding the show that has the most users (i.e. my users favorite TV show) with my `Show` and `User` model having a `has many, through` relationship? Almost as if the Flatiron Gods knew I would run into this problem, I remembered I had just finished a lab with similar querying requirements. Joining `Show` and `User` together, I could group all shows and return a count of how many users each show had.

After that, it was smooth sailing to the finish line!


