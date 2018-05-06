# Javascript - AJAX

## Lesson Objectives

1. Explain AJAX
1. Demonstrate jQuery AJAX
1. Explain promises
1. Explain Cross Site AJAX
1. Explain JSONP
1. Explain CORS

## Explain AJAX

## Demonstrate jQuery AJAX

```html
<!DOCTYPE html>
<html>
	<head>
		<title></title>
		<script type="text/javascript" src="http://code.jquery.com/jquery-1.11.3.min.js"></script>
	</head>
	<body>
		hi
		<script type="text/javascript">
			$(function(){
				$.ajax({
					url:'http://www.omdbapi.com/',
					method: "GET",
					data: { s: "star wars" },
					success: function(data, status, jqXHR){
						console.log(data);
					},
					error: function(jqXHR, status, error){
						console.log('bad');
					}
				});
			});
		</script>
	</body>
</html>
```

## Explain promises

```html
<!DOCTYPE html>
<html>
	<head>
		<title></title>
		<script type="text/javascript" src="http://code.jquery.com/jquery-1.11.3.min.js"></script>
	</head>
	<body>
		<script type="text/javascript">
			$(function(){
				var promise = $.ajax({
					url:'http://www.omdbapi.com/',
					method: "GET",
					data: { s: "star wars" }
				});
				promise.done(function(data){
					console.log(data);
				});
				promise.fail(function(data){
					console.log('fail!');
				});
				promise.always(function(data){
					console.log('always!');
				});
			});
		</script>
	</body>
</html>
```

more succinct with extra done:

```html
<!DOCTYPE html>
<html>
	<head>
		<title></title>
		<script type="text/javascript" src="http://code.jquery.com/jquery-1.11.3.min.js"></script>
	</head>
	<body>
		<script type="text/javascript">
			$(function(){
				$.ajax({
					url:'http://www.omdbapi.com/',
					method: "GET",
					data: { s: "star wars" }
				})
				.done(function(data){
					console.log(data);
				}, function(data){
					console.log('another done');
				})
				.fail(function(data){
					console.log('fail!');
				})
				.always(function(data){
					console.log('always!');
				});
			});
		</script>
	</body>
</html>
```

custom deferred and promise objects:

```html
<!DOCTYPE html>
<html>
	<head>
		<title></title>
		<script type="text/javascript" src="jquery-1.11.3.min.js"></script>
	</head>
	<body>
		<script type="text/javascript">
			var deferred = $.Deferred();
			var promise = deferred.promise();
			setTimeout(function(){
				deferred.resolve("first promise");
			}, 1000);

			var deferred2 = $.Deferred();
			var promise2 = deferred2.promise();
			setTimeout(function(){
				deferred2.reject("second promise");
			}, 5000);

			promise.fail(function(value) {
				console.log('fail first: ' + value);
			}).always(function(value){
				console.log('always first: ' + value);
			}).done(function(value){
				console.log('done first: ' + value);
			});

			$.when(promise, promise2)
			.done(function(value1, value2){
				console.log('done both: ' + value1 + ", " + value2);
			}, function(value1, value2){
				console.log('2nd done both: ' + value1 + ", " + value2);
			})
			.then(function(value1, value2){
				console.log('then both success: ' + value1 + ", " + value2);
			}, function(value1, value2){
				console.log('then both fail: ' + value1 + ", " + value2);
			})
		</script>
	</body>
</html>
```

## Explain Cross Site AJAX

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
