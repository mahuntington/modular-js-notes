## Explain Cross Origin AJAX

```javascript
$.ajax({
	url: 'https://status.github.com/api/status.json',
	success: function(data) { console.log(data) },
	error: function(jqXHR, status, errorThrown){ console.log(status); }
});
```

look at console

## Explain JSONP

```html
<!-- Request sent via a script tag -->
<script src="https://status.github.com/api/status.json?callback=apiStatus"></script>
<!-- Data received as an execution of the predefined function. -->
<script> function apiStatus(data) { console.log(data.status); } </script>
```

## Explain CORS

1. http://www.omdbapi.com/?s=pirates&r=json
1. `Access-Control-Allow-Origin:*`
