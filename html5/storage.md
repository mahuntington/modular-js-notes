# Web Storage

## Lesson Objectives

1. Describe web storage
1. Differentiate between localStorage and sessionStorage
1. View storage in dev tools
1. Set an item
1. Get an item
1. Remove an item
1. Clear the storage
1. Store objects/arrays
1. Retrieve objects/arrays

## Describe web storage

Web storage is like cookies, but it doesn't get transmitted to the server.  It's more secure, more performant, and the storage limit is larger (5MB per origin).

The format is key value pairs, both of which are strings

## Differentiate between localStorage and sessionStorage

- localStorage lives on until deleted
- sessionStorage ends when the user closes the window

## View storage in dev tools

1. Open up dev tools and click on "Application"

    ![](https://i.imgur.com/96hed8l.png)

1. Expand Local Storage and Session Storage

    ![](https://i.imgur.com/e2tgdO3.png)

1. Click on one of the DBs to view its contents

    ![](https://i.imgur.com/HZiwigZ.png)

## Set an item

```javascript
localStorage.setItem('foo', 'bar');
sessionStorage.setItem('age', 2); //note this will be converted to a string
```

## Get an item

```javascript
localStorage.getItem('foo'); //'bar'
sessionStorage.getItem('age'); //2 - note this is a string, even though, it was set as a number
```

## Remove an item

```javascript
localStorage.removeItem('foo');
sessionStorage.removeItem('age');
```

## Clear the storage

```javascript
localStorage.clear();
sessionStorage.clear();
```

## Store objects/arrays

```javascript
localStorage.setItem('myObj', {foo:'bar'});
```

This doesn't work:

![](https://i.imgur.com/3BgVNj9.png)

Instead you have to convert objects and arrays into strings:

```javascript
localStorage.setItem('myObj', JSON.stringify({foo:'bar'}));
localStorage.setItem('myArray', JSON.stringify([1,2,'apple']));
```

![](https://i.imgur.com/LfnErPb.png)

## Retrieve objects/arrays

After, `JSON.stringify()`, the arrays/objects are stored in local/session storage as strings.  To get them back into variables, use `JSON.parse()`:

```javascript
const myObj = JSON.parse(localStorage.getItem('myObj'));
const myArray = JSON.parse(localStorage.getItem('myArray'));
```
