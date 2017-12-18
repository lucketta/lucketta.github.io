---
layout: post
title:      "Troubleshooting Techniques for Deploying to Heroku"
date:       2017-12-18 03:33:41 +0000
permalink:  troubleshooting_techniques_for_deploying_to_heroku
---


My previous blog post, [Setting up Rails BackEnd/ReactJS FrontEnd Project and Heroku](http://areannaluckett.org/setting_up_rails_backend_reactjs_frontend_project_and_heroku), explained how I connected my Rails backend to a ReactJS frontend and deployed that project to Heroku. In my next few blogs I will break down the code and commands I used to deploy to Heroku and illustrate how I troubleshooted common issues:

In Step 10, we set the buildpack order by typing two commands into the command line. What are buildpacks? According to the Heroku Documentation:

> Buildpacks are responsible for transforming deployed code into a slug, which can then be executed on a dyno. Buildpacks are composed of a set of scripts, and depending on the programming language, the scripts will retrieve dependencies, output generated assets or compiled code, and more. This output is assembled into a slug by the slug compiler.
> 
> Heroku’s support for Ruby, Python, Java, Clojure, Node.js, Scala, Go and PHP is implemented via a set of open source buildpacks.

Since we are running two servers with the Rails backend and ReactJS frontend, we will need buildpacks for each language used: Ruby and NodeJS.

If you ever need to check your buildpacks you can run the command below:


```heroku buildpacks
```

As always, it is better to use official buildpacks listed on Heroku to make sure your code will be compiled correctly. You can find a list of official builds [here](https://devcenter.heroku.com/articles/buildpacks).


Another issue I ran into is not  specifying a node version and npm version. 

> Your production environment should mirror your development environment, especially in the case of important binaries. First, check your local versions:
> 
> $ node --version
> 
> $ npm --version
> 
> Then, compare the results with your package.json engines section.

If your package.json section doesn't include a node or npm version, specify it, push up to your git repo and then to Heroku.


Check back on my blog as I work my way through other common problems!


