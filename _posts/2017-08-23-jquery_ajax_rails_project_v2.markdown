---
layout: post
title:  "jQuery/Ajax Rails Project v2"
date:   2017-08-23 01:47:09 +0000
---


The goal of this project was to update my existing rails portfolio project, [Chill Flix](https://github.com/lucketta/chill-flix-rails-portfolio-project), to include jQuery and Ajax requests to update the DOM without a page refresh.

Feel free to read my last blog post to get a more in-depth explanation of the initial project, [here](http://areannaluckett.org/2017/07/08/activerecord_query_in_rails_portfolio_project/). In short, I wanted to create a webapp that allows users to keep track of their favorite TV shows.

The requirements for this project were to:
* Include a show resource rendered using jQuery and an Active Model Serialization JSON backend.
* Include an index resource rendered using jQuery and an Active Model Serialization JSON backend.
* Include at least one has_many relationship in information rendered via JSON and appended to the DOM.
* Use your Rails API and a form to create a resource and render the response without a page refresh.
* Translate JSON responses into JS Model Objects.
* At least one of the JS Model Objects must have at least one method added by your code to the prototype.

I definitely had a lot of fun with this project, especially at the end, when I was all finished, and realized this is how web pages are built. How exciting! To have gone from not knowing how the internet works, to being able to create my own dynamic web app has been an awesome journey.

Like everyone else in the coding world, however, I did run into a particulary challenging bug:

Each TV show page allows a user to submit a review and their username. My job was to code this functionality by appending a JSON object using content from the form to the DOM without a page refresh. 

First, I created the form. I then used Javascript to create a listener for the form submit and used a Jquery.post call to load data from the server. After serializing the data and pushing that data to the post request, I was finding that I was getting back the HTML of the whole page instead of the JSON object. 

For those of you who have run into that problem, here is a quick tip:

![](http://imgur.com/bupmwen.png)

This is the low level call using Ajax that will allow you to set a datatype to JSON and that will render a JSON object, instead of receiving HTML. From there, I was able to create a new record in my model and append that object to the DOM.

With just one more major project to go before I finish the curriculum, I am super excited to learn what React and Redux have in store for me.


