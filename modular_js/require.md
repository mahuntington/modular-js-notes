# RequireJS

## Installation

Download from [the download page](http://requirejs.org/docs/download.html).

## Set up

`index.html:`

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
    <head>
        <script data-main="js/main.js" src="js/require.js"></script>
    </head>
    <body>

    </body>
</html>
```

This loads require.js and tells it to load `js/main.js`:

```javascript
requirejs(['js/footer.js'], function(footer) {
    console.log(footer);
});
```

This says to run the code inside the function, once `js/footer.js` has loaded.  The exported value of `js/footer.js` will be passed into the function as the variable `footer`.  Let's create `js/footer.js`:

```javascript
define(['js/sizes.js'], function(sizes){
    return {
        height:sizes.small,
        width:sizes.medium
    }
});
```

The first parameter defines any dependencies that must load before this file runs.  Whatever gets returned in the function that is passed into `define()` as the second param, will be what that file "exports" to files that include it.  In this case, that object becomes `footer` in `js/main.js`.

Finally, let's define `js/sizes.js`:

```javascript
define(function(){
    return {
        small: 100,
        medium: 200,
        large: 300
    }
})
```

This file has no dependencies
