## Explain Cross Origin AJAX

```javascript
$.ajax({
	url: 'http://api.flickr.com/services/feeds/photos_public.gne?jsoncallback=processJSON&tags=monkey&tagmode=any&format=json',
	success: function(data) { console.log(data) },
	error: function(jqXHR, status, errorThrown){ console.log(status); }
});
```

look at console

## Explain JSONP

```html
<!-- Create a function that will be called -->
<script> function processJSON(data) { console.log(data); } </script>
<!-- Request sent via a script tag -->
<script src="http://api.flickr.com/services/feeds/photos_public.gne?jsoncallback=processJSON&tags=monkey&tagmode=any&format=json"></script>
```

## Explain CORS

1. http://www.omdbapi.com/?apikey=53aa2cd6&s=pirates&r=json
1. `Access-Control-Allow-Origin:*`
