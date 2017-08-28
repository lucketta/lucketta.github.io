---
layout: post
title:  "React/Redux: Game of Thrones Quote Generator"
date:   2017-08-28 03:26:38 +0000
---


My last and final project revolved around using React and Redux to build my app. I decided to go with something a little fun this time around: Game of Thrones Quote Generator. I found a very cool API, [here](https://github.com/wsizoo/game-of-thrones-quotes), that spits out quotes from different characters from the show (and because there are just so many, don't feel bad if you don't recognize a name). 

You can find my repository [here](https://github.com/lucketta/got-quote-generator), but beware, especially if you haven't watched the show, GoT is mildly inappropriate so click for new quotes at your own risk :)

The way I approached this project, led slightly by the API was to create two avenues to get a quote. One is just a rapid fire quote generator that lets you receive a quote randomly. The API also lets you search the quotes using a character name, so the second avenue is being able to click on specific characters from a list with their photos to see a quote from that character.

Snapshot of the app:
![](http://i.imgur.com/AA8n2vh.png)

One of the problems I ran into in this project, was figuring out how to render a component separately. When a user clicks on a character to get their quote, the quote would show up on the top of the page pushing down the character list. The functionality I wanted to implement is when you click on a character, you go to a separate "page" and it renders just the quote and the character name.

To render components separately you must use Switch. Switch can be implemented using the DOM bindings for React Router. To install, type the following in your terminal:

```
npm install --save react-router-dom
```

then at the top of your component file:
```
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
```
 

Then, using the example from [A Simple React Router v4 Tutorial](https://medium.com/@pshrmn/a-simple-react-router-v4-tutorial-7f23ff27adf) to illustrate my point:

```
 <Switch>
   <Route exact path='/' component={Home}/>
   <Route path='/roster' component={Roster}/>
	 <Route path='/schedule' component={Schedule}/>
</Switch>
```

Switch will render the first Route that matches, exclusively, allowing only the elements you want to render to be shown on the page. And voila, problem solved!

Feel free to check out my project and thank you for reading!
