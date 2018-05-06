# DOM EVENTS

## LESSON OBJECTIVES

1. Describe what a browser event is
1. Create a click event
1. Use a named, referenced function as the click handler for the listener
1. Create a custom event

## Describe what a browser event is

Interacting with the page (`events_example`)

Every kind of interactivity in the browser is an event: clicks, mouseovers, key presses, scrolling, resizing, loading the page, and more.

When you interact with the browser it checks to see if there is a _listener_ for that interaction.

If there is a _listener_ present, the browser will try to run any _handlers_ for those interactions.

A _handler_ is just a function that runs a desired procedure.

## Create a click event

How can we set up a _click_ event?

We need:

1. An element to set it on
2. A _listener_ that listens for the event: on _which element_ should the event take place
3. A _handler_ that runs the procedure we want to have happen when the event is triggered

Make a button in the html:

```html
<button id="btn">Click me<button>
```

Grab the button in the JS (DOM element):

```javascript
const $btn = $('#btn');
```

### Event listener

Set an event listener:

Use `.on()` [.on() documentation](http://api.jquery.com/on/)

```javascript
$btn.on('click');
```

The event listener takes a string as an argument. There are just a few strings that it will recognize as valid events, and 'click' is one of them.

[List of events](https://developer.mozilla.org/en-US/docs/Web/Events)

### Event handler

Add a _function_ that runs what we want to have happen. This function is what _handles_ the event and is called an _event handler_:

```javascript
$btn.on('click', () => {
	console.log('button was clicked!!');
});
```

Notice that we have supplied a function as an argument. The jargon for using a function as an argument to another function is `callback`.

pseudo code for an event listener

```javascript
elem.on(STRING, CALLBACK);
```

### Add Text to the Page on Click

```javascript
$btn.on('click', () => {

	$('body').append("It seems as if it has been clicked!");

});
```

### Activity

* Add a button to your `index.html` with an id of `btn`

* Make it so that when you click the button, a console.log will appear in your browser's javascript console that says `My click event works!!!`

* Whenever you make a click event, always test it with a console.log to make sure that it works.

### Extra Activity

* Make it so that when the button is clicked, a message will appear on the page instead of just inside the console. _example:_

Create a paragraph inside the click handler:

```javascript
const $p = ('<p>').text("Here is some text!!!!!");
```

Append the paragraph to the page:

```javascript
$('body').append($p);
```

### Extra Activity

* Make it so that when the button is clicked, an image will appear on the page.

### Extra Activity

* Experiment with setting more than one listener on the same element. How would you go about doing that?

## Use a named, referenced function as the click handler for the listener

The _handler_ that we used for our click was _anonymous_. It was a function that had no name. We just told the listener to run an _anonymous_ function. We can give our function a name and thereby reuse that function with other event listeners.

Here is the pattern we have already seen:

```javascript
<button id="btn">Click for message</button>
```

```javascript
const $btn = $('#btn');

$btn.on('click', () => {
	const $p = $('<p>').text("THE EARTH IS ROUND");
	$('body').append($p);
});
```

### Named Function

We can abstract the anonymous function out and give it a name:

Separate function, not inside the listener:

```javascript
const addText = () => {
	const $p = $('<p>').text("THE EARTH IS AN OBLATE SPHEROID");
	$('body').append($p);
}
```

We can then reference it in the event Listener:

```javascript
$btn.on('click', addText);
```

With a named function, we can use the same handler for more than one DOM element.

### Referenced Function

Note that we do not invoke the function with parentheses. We do not want to invoke the function right away, we merely want to _reference_ it to be invoked when the listener runs it.

* The function should be defined before it is used in the event listener
* When the function is invoked inside the event listener **leave out the parentheses**. We do not want to invoke the function right away! We merely want to reference that function in the listener.

Here the function is invoked and will run immediately:

```javascript
$btn.on('click', addText());
```

We don't want this! We only want the function to run when the user has clicked on the button.

Complete code:

```javascript
const $btn = $('#btn');

const addText = () => {
	const $p = ('<p>').text("THE EARTH IS AN OBLATE SPHEROID");
	$('body').append($p);
}

$btn.on('click', addText);
```

Let's do something fancier, and toggle the background-color of the page using `.toggleClass()`

```javascript
const changeClass = () => {
  $('body').toggleClass('black');
}

$('#btn').on('click', changeClass);
```

CSS:

```css
.black {
  background-color: black;
}
```

### Activity (15 min)

* Separate an anonymous handler function from one of your event listeners, and make it a named function instead.  
* Make it so that the named handler will run when the button is clicked. (Remember to make sure the function is _referenced_ and not _invoked_ when you set it on the listener).
* Make it so that the click will work only after the user has clicked.

**Extra Activity**

Make it so each time click the button, that background-color of the page will toggle.

**Extra Activity**

* Add yet another button, and make it so that when this extra button is clicked, it will run the exact same handler as your previous button.

**Extra Activity**

* Make it so that when you click either of these buttons, an image will toggle on and off the page. There is no toggleImage method so you'll have to do it programmatically. Click once = message appears. Click again = message disappears. Click again = message reappears, etc. _Hint:_, you can use a global variable boolean and toggle it upon click.

### Ask (5 min)

* What is the difference between a named vs anonymous function?
* What is the difference between an invoked vs a referenced function?
* What is the difference between an event listener and an event handler?
* When would you want to use a named function over an anonymous one?

### EXTRA: mouseenter and mouseleave

There is a special jQuery method for hover. We can replicate it using `.on()` by making an event for `mouseenter` and a separate event for `mouseleave`

```javascript
  $('#some-div').on('mouseenter', function() {
    $('body').css('background-color', 'red');
  });

  $('#some-div').on('mouseleave', function() {
    $('body').css('background-color', 'white');
  });
```

* How would we re-arrange this to make our anonymous functions named functions?

## Create a custom event

You can even create your own custom events

```javascript
$( "#foo" ).on( "custom", function( event, param1, param2 ) {
  alert( param1 + "\n" + param2 );
});
$( "#foo").trigger( "custom", [ "Custom", "Event" ] );
```
