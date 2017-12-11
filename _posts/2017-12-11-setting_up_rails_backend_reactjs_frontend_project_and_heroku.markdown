---
layout: post
title:      "Setting up Rails BackEnd/ReactJS FrontEnd Project and Heroku"
date:       2017-12-11 13:51:41 -0500
permalink:  setting_up_rails_backend_reactjs_frontend_project_and_heroku
---


Starting a new project is exciting, but can also feel like a monumental task when trying to pair different languages and frameworks together. Today, I will show you the steps and code I used to successfully create a Rails backend and ReactJS frontend, as well as the settings needed to make sure your project compiles and can be pushed up to Heroku.

There were many resources on the internet for different aspects of this process, but there wasn't a guide that easily listed each step and helped with the somewhat difficult task of pushing to Heroku. Here is what I did and I hope it works for you!


**Step 1: New Rails Project**

You will need to create a new Ruby on Rails project. Note: Heroku doesn't support Sqlite3, the default option when starting a new Rails project, so we will specify our database to use Postgresl.

 `rails new [insert name of project] --database=postgresql --webpack=react --skip-coffee`
 
 
**Step 2: Set up Git Repo**
 
Create a new git repo for this project for code management. An easy google search will show you how to do this. Usually, I create a new repo on my Github account then connect it to my local environment.
 

**Step 3: ReactJS FrontEnd**

Our frontend will be using the ReactJS framework. To install:

`npm install -g create-react-app`

Then create your new ReactJS project with your own name for <my-app>:

`create-react-app my-app`


**Step 4: Package.json Client Side Port Change**

Because our Rails app will act like an API, we will run the client side on port:3001 and the backend on port:3000 and start them up together. So, in our package.json file in the** React client folder**, add the following line:

    `"proxy": "http://localhost:3001"`
		
		
**Step 5: Procfiles**

We are going to create two Procfiles (for Heroku) to fire up both servers together:

Create a new file in the root directory of your project called >> Procfile:

    `web: bundle exec rails s`
		
	
Create a new file in the root directory of your project called >> Procfile.dev:

    `web: cd client && PORT=3000 npm start
      api: PORT=3001 && bundle exec rails s`
			

**Step 6: Foreman**

Install the gem: Foreman, bundle install/update. This will allow us to fire up both the server and client side code running on different ports using the commands from our Procfile.


**Step 7: Start.rake**

During deployment, we need Foreman to start our servers. An easy way to do this is to automate the process. We are going to be using a code snippet from a great article, "[A Top Shelf Web Stack—Rails 5 API + ActiveAdmin + Create React App",](https://medium.com/superhighfives/a-top-shelf-web-stack-rails-5-api-activeadmin-create-react-app-de5481b7ec0b) by [superhighfives](https://medium.com/superhighfives).

Create a start.rake file in lib/tasks: 

```
namespace :start do
      task :development do
        exec 'foreman start -f Procfile.dev'
      end

      desc 'Start production server'
      task :production do
        exec 'NPM_CONFIG_PRODUCTION=true npm run postinstall && foreman start'
      end
    end

    desc 'Start development server'
    task :start => 'start:development'
```


**Step 8: Scripts in package.json root**


In our package.json root (not the client package.json) we want to add a couple of scripts so that during deployment in Heroku we have everything we need installed and built:

```
  "build": "cd client && npm install && npm run build && cd ..",
   "deploy": "cp -a client/build/. public/",
   "postinstall": "npm run build && npm run deploy"
```


**Step 9: New Heroku Project**

*Head to the Heroku site and make you set up your environment first by following the directions so that the following commands work.*

We are now going to create a new Heroku project, so that we can test our webapp in a production environment. It's a lot easier to do this setup now, before writing too much code in your app to work out any errors and kinks early.

In the command line, start a new Heroku project:

```
heroku apps:create [insert name here]
```


**Step 9a: Rename Heroku Project**

You can rename your project by using the command: 

`heroku apps:rename newname`


**Step 10: **

The next few commands are going to set a few options to make sure when you deploy to Heroku it is successfull. We will also be setting the order of our buildpacks for node and ruby:

Run each commands separately: 
```
heroku config:set NPM_CONFIG_PRODUCTION=false
heroku buildpacks:add heroku/nodejs --index 1
heroku buildpacks:add heroku/ruby --index 2
```


**Step 11:  Pushing up to Heroku**

Make sure that you have pushed all new changes to your git repo. Then push your new app to Heroku:

`git push heroku master`


**Step 12:  All Done**

That should be it. Do a happy dance because watching your app push to Heroku is pretty intense, especially after many failed attempts. I hope this guide helps you get overt his hump!

Happy Coding!
