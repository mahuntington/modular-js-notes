# Online/Offline Events

One of the new HTML 5 things you can do is tell when the user loses connection.  Here's an example:

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
    <head>
        <meta charset="utf-8">
        <title></title>
        <script src="https://code.jquery.com/jquery-3.3.1.min.js" charset="utf-8"></script>
        <script type="text/javascript">
            $(function(){
                $(window).on('offline', function(){
                    console.log('offline!');
                });
                $(window).on('online', function(){
                    console.log('online!');
                });
            })
        </script>
    </head>
    <body>

    </body>
</html>
```

You can do this for apps that let the user work without connection and then update when connection is reestablished
