# DOM Input

### LESSON OBJECTIVES
_after this lesson, students will be able to:_

1. Capture text input from the browser
1. Use a form's submit event
1. Build a list from input

## Capture text input from the browser

Provide a means for the user to provide input, and capture that input with an event handler.

Make an input field and a button in index.html

```javascript
<input type="text" id="input-box" />
<input type="submit" id="submit-btn" />
```

Set an event on the submit

```javascript
$('#submit-btn').on('click', () => {
  console.log('clicked');
});
```

Make it so the handler grabs the value inside the input box (and logs it to check)

Use jQuery `.val()`

```javascript
$('#input-box').val()
```

```javascript
  $('#submit-btn').on('click', () => {
    console.log('clicked');  
    console.log( $('#input-box').val() );
  });
```

## Use a form's submit event

With a **form** tag you can hit the enter key to submit the form data.

```javascript
<form>
    <input type="text" placeholder="enter your name" id="input-box"/>
    <input type="submit" value="SUBMIT"/>
</form>
```

Set the handler on the form element instead of the submit.

```javascript
  $('form').on('submit', () => {
    console.log('clicked');  
    console.log( $('#input-box').val() );
  });
```

### Prevent default refresh

When you submit the form, the default action is to refresh the page. Let's prevent this default behavior using the freebie `event`.

```javascript
  $('form').on('submit', (event) => {
    console.log('clicked');  
    console.log( $('#input-box').val() );
    event.preventDefault();
  });
```

### Reset your input field

`.trigger()` can trigger events on elements (click, hover, etc).  The `reset` event clears a text input

```javascript
$(elem).trigger('reset');
```

```javascript
  $('form').on('submit', (event) => {
    console.log('clicked');  
    console.log( $('#input-box').val() );
    event.preventDefault();
    $(event.currentTarget).trigger('reset');
  });
```

## Build a list from input

Make a nonsense list to store any kind of nonsense

* Make a `list` array where nonsense data will be stored
* Push input into the list
* Run a function **render** that will render items in the list.

```javascript
const list = [];

$('form').on('submit', (event) => {
  console.log('clicked');  
  console.log( $('#input-box').val() );

  list.push( $('#input-box').val() );

  event.preventDefault();
  $(event.currentTarget).trigger('reset');

  render();
});
```

* Make **render** function to iterate over all items in the list

```javascript
const render = () => {
  console.log('render everything in the list');
  console.log('list: ', list);
  list.forEach((item) => {

    console.log(item);

  });
}
```

* Let's build in some `ul`s for the list items

  ```html
  <ul></ul>
  ```

* Make a list item for every item in the array

```javascript
const render = () => {
  console.log('render everything in the list');
  console.log('list: ', list);
  $('ul').empty();
  list.forEach((item) => {    
    $('ul').append('<li>' + item + '</li>');
  });
}
```

![](https://i.imgur.com/vjQ2Bu9.png)

* Add an event listener to each item that calls on one single event handler

```javascript
list.forEach((item) => {    
  const $li = $('<li>' + item + '</li>');
  $li.on('click', doNonsense);
  $('ul').append($li);      
});
```

```javascript
const doNonsense = (event) => {
  console.log('item clicked: ', event.currentTarget);
  $(event.currentTarget).css('background-color', 'red');
}
```
