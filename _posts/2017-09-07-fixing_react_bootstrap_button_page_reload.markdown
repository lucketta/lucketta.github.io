---
layout: post
title:  "Fixing React Bootstrap Button Page Reload "
date:   2017-09-07 02:40:30 +0000
---

An interesting problem I ran into using React Bootstrap components was figuring out how to stop page reloads while using navigation items, like `Button` links, `Nav`, `NavItem`, etc.

Imagine, in your project, you are using React Bootstrap's Button component to link to a new 'page'. On every click your app successfully routes to a new 'page' but you notice a page refresh.

What should you do?

First understand that navigation items in React Bootstrap are actually forms submitting requests for a new route (in this case), so, of course, there will be a page reload. 

## Solution # 1

The first solution to this issue is to bind an onClick action to the button to prevent page reloads using preventDefault. Take a look at the following example to see how this is implemented:

```
class YourComponent extends Component {

  handleOnClick(event) {
    event.preventDefault();
    }

  render(){
    return (
      <div>
         <Button onClick={event => this.handleOnClick(event)}>Click Me</Button>
	  </div>
  )}
 }
```

## Solution # 2
Another solution I found is to use ```Link``` from react-router-dom. You can find the documentation [here](https://github.com/ReactTraining/react-router/blob/master/packages/react-router-dom/docs/api/Link.md). Link does not automatically reload the page. 

I used this option instead of ```Button``` because I did not have access to history to push a new route. Using ```Link``` allowed me to change the route without an automatic page reload which worked better for my project than ```Button``` could. An example of the syntax is below:

Make sure to import Link:
```
import { Link } from 'react-router-dom';
```

Then, in your component:

```
<Link to="/home">Home</Link>
```

Simple as that.

Now you've seen two solutions to work around automatic page reload with certain components. Hope this helps with this small, but interesting issue I found while building my React front-end app. 
