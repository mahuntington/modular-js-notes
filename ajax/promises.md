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
					url:'http://www.omdbapi.com/?apikey=53aa2cd6',
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
					url:'http://www.omdbapi.com/?apikey=53aa2cd6',
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
