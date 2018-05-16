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
					url:'http://www.omdbapi.com/?apikey=53aa2cd6',
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
