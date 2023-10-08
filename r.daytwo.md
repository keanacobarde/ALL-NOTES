---
id: 23k5vmwq7bo0ftxtykskeyb
title: Daytwo
desc: ''
updated: 1696792060077
created: 1696686177991
---

## To Leave At the Door
- *The men who hate their gfs*
- *Him. Ugh.*
- *Everything that went down last night : D !*
- *The idea that I'm behind. I am not behind. I just am as I am.*

## Agenda
- *Watching E23 presentations*
- *Recreating the Joke Generator in React*
- *Routing is on Monday*
- *Going over the counter application*
- *Going over Joke Generator*

## Counter
> NOTE: You missed the authentication part, but you don't need to yet. Just a note - most of your templates include authentication. Incorperating FireBase is a little bit of an extra step, though.

Counter Components 

![Alt text](image-3.png)

Since you weren't really able to follow along, here's some of the steps that you missed on Saturday:

1. Converting the Counter functionality and styling into a component of its own.

> Some of the issues I encountered:

- Understanding how to call on and use props. Had to look back at the Joke Generator to figure this out. What is passed through the component function, deconstructed - is a prop. Examples: 

An example of props used when components are called upon.

```
      <Counter title={"Keana's Counter"} />
      <Counter title={"Salem's Counter"} />
      <Counter title={"Everyone's Counter"} />
```

An example of props, when introduced to a component function. 

```
export default function Counter({ title }) 
```
- Remember: each component has access to its own prop object. There is only one prop object per component. You also, TS style, need to specific the data types of props within propType objects. An example: 

```
Counter.propTypes = {
  title: PropTypes.string,
};

Counter.defaultProps = {
  title: 'Counter',
};
```
- I struggled with event handler functionality. I continued to get a stack overflow-esque error whenever I attempted to utilize if, else statements. Switched the switch cases and received same result - what I was missing was setting an anonymous function within the onClick invokation. Example: 

```
const handleClick = (action) => {
    switch (action) {
      case 'Increment':
        counter((prevState) => prevState + 1);
        break;
      case 'Decrement':
        counter((prevState) => prevState - 1);
        break;
      case 'Reset':
        counter((prevState) => prevState - prevState);
        break;
      default:
        break;
    }
  };
  return (
    <div
      className="text-center d-flex flex-column justify-content-center align-content-center"
      style={{
        height: '90vh',
        padding: '30px',
        maxWidth: '400px',
        margin: '0 auto',
      }}
    >
      <h1> {title} </h1>
      <h1> {counterValue} </h1>
      <button type="button" onClick={() => handleClick('Increment')}> Increment </button>
      <button type="button" onClick={() => handleClick('Decrement')}> Decrement </button>
      <button type="button" onClick={() => handleClick('Reset')}> Reset </button>
    </div>
  );
```

Notice:
```
onclick={() => handleClick('action')}
```
You left out the anonymous function declaration and just incoked the handleClick function, created outside to return block. I'm still not entirely sure why this is needed; however, it mirrors the need for a function invokation within an eventListener. For now, use this methodology until it doesn't work. 


## Counter - In Summary
> Teaches you the basics of creating components, setting prop types, and creating event handlers. It is a good introduction to how React reduces the complexity of manipulating the DOM through the creation of components. You struggled a lot with basic principles, but it looks like you're gaining some fluency. Continue to use this lesson as a guide in the future.


## Aside - Pizza Menu

> Further cementing your understanding of components and React's repeatablility. There was once a separation - each file controlled its own segment of development. CSS for styling. HTML for structure. JS for functionality. However, as you began seeing in your traversal through Vanilla JS - JS started taking control over many aspects of HTML. Very quickly, you began dynamically rendering HTML through the usage of DOM manipulation in JS files. Think back to old projects where this happened: 

_Git Sub_

> Setting the HTML to be rendered in the Overview within the JS file - NOT the HTML file.

```
const aboutMe = () => {
const domString = `<div style="font-family:'Courier New'; margin: 0.7rem 0 0 0.5rem;"><h6 style="display:flex;"><span class="material-symbols-outlined">
stadia_controller
</span>gregGroks13/greg.md</h6>
<h1>👋 Hi, I'm Greg...</h1>
<hr>
</div>
<div class="aboutme-header-img">
<img class="aboutme-header-img" style="margin: 1rem;" src="assets/images/github-header-image.png">
</div>
<div style="font-family:'Courier New';padding:0.5rem;"><p>
As a software engineer, I bring a unique blend of capabilities to the digital realm. Here's what I'm all about:
Problem-Solving Wizardry 🧙‍♂️<br><br>

Got a complex challenge? I thrive on breaking down problems into bite-sized pieces and crafting elegant solutions. My algorithmic prowess helps me navigate through the maze of logic to find the optimal path.
Multilingual Maestro 💬<br><br>

Whether it's Python, JavaScript, Java, or even the nuances of SQL, I'm fluent in a multitude of programming languages. I love conversing with code and turning abstract ideas into functional systems.
End-to-End Enlightenment 🌐<br><br>

From the front-end dazzle to the back-end stability, I've got your software's entire journey covered. Crafting user-friendly interfaces is my jam, and optimizing databases is my delight.
Learning at Lightspeed 🌟<br><br>

The tech world evolves faster than lightspeed travel, but that's where I thrive. I adapt to new technologies, frameworks, and tools like a digital chameleon, ensuring that your software stays at the cutting edge.
Collaborative Cohort 🤝<br><br>

Teamwork makes the code work! I seamlessly integrate into development teams, communicating ideas, sharing insights, and contributing effectively to ensure the collective success of projects.
Let's Code the Future! ⏩<br><br>

Whether you need a quick bug fix or a comprehensive software solution, I'm here to assist. Let's collaborate and create digital marvels that redefine the boundaries of possibility!</p></div>`
renderToDom(".aboutMe", domString); 
}
```

This is an example of how stupidly clunky rendering to the DOM dynamically can get. This is why React exists - to leverage the control JS has over the DOM...without having to interact with the DOM at all!

## Joke Generator
Joke Generator - Example of UseEffect

![Alt text](image-4.png)

Joke Generator - Example of Ternary Button Functionality
![Alt text](image-5.png)

Decided Against A useEffect() 

![Alt text](image-6.png)

Joke funny funny 

![Alt text](image-7.png)

State 

![Alt text](image-8.png)

### Joke Generator - My Attempt

> components/Joke.js

```
import React from 'react';
import PropTypes from 'prop-types';

export default function Joke({ joker, btnText }) {
  return (
    <div>
      <h2> { joker.setup } </h2>
      <h2> {btnText !== 'Get a Punchline' ? joker.delivery : ''} </h2>
    </div>
  );
}

Joke.propTypes = {
  joker: PropTypes.shape({
    setup: PropTypes.string,
    delivery: PropTypes.string,
  }).isRequired,
  btnText: PropTypes.string.isRequired,
};

```

*Code Snacks - Bits of code that I didn't understand*


> pages > index.js

```
import { useState } from 'react';
import Joke from '../components/Joke';
import getJoke from '../api/jokeData';

function Home() {
  const [joke, setJoke] = useState({});
  const [btnText, setBtnText] = useState('Get A Joke');

  const getAJoke = () => {
    getJoke().then((obj) => setJoke({
      setup: obj.setup,
      delivery: obj.delivery,
    }));
    setBtnText('Get a Punchline');
  };

  return (
    <div
      className="text-center d-flex flex-column justify-content-center align-content-center"
      style={{
        height: '90vh',
        padding: '30px',
        maxWidth: '400px',
        margin: '0 auto',
      }}
    >
      <h1>Get a Joke!</h1>
      <Joke joker={joke} btnText={btnText} />
      {btnText === 'Get A Joke' || btnText === 'Get A New Joke' ? (<button type="button" onClick={getAJoke}> {btnText} </button>) : (<button type="button" onClick={() => setBtnText('Get A New Joke')}> {btnText} </button>) }
    </div>
  );
}

export default Home;
```

*Code Snacks - Bits of code that I didn't understand*


# Simply Books

> Setup is due Monday 

## Hooks - What are they? 

They help hook into the state/other aspects of React. You're hooking into the data and performing some sort of functionality on it. 

## Hooks in Next JS

Don't ever touch the next.js config. Use the regular image tag and then disable the linter error for the entire file.


Dynamic Routing

![Alt text](image-9.png)