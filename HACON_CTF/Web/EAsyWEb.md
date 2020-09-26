# EAsy WEb

> Go on, step by step,
And you have the flag!!
https://murmuring-caverns-26740.herokuapp.com/

We are greeted by a simple login screen with a header of `Okay, now let's start finding the flag`:

![webPage](Images/EasyWeb/webPage.png)

First step of any web challenge is to check the source code(Ctrl+U)
```html
<!DOCTYPE html>
<html>
<head>
	<title>
		New Page
	</title>
	<style>
		body {
			background-color: white;
		}
		h1 {
			color: blue;
		}
	</style>

	<!-- <script>
		function myfunc() {
			alert("1");
			let uname = document.getElementById('user').value;
			let ppass = document.getElementById('pass').value;
			//console.log("uname = ",uname, " pass = ", ppass);
			let data  ={
				username: uname,
				password: ppass
			}
			console.log("data = ",data);
			$.post("/",data)
				.done(function(result) {
					alert(result);
				})
		}
	</script> -->
	</head>
	<body>
		<h1>Okay, now let's start finding the flag</h1>

		<form>
			<label for="username">Username</label>
			<input type="text" name="username" id="user"><br>
			<label for="password">Password</label>
			<input type="text" name="password" id="pass"><br>
			<input type="button" name="button" id="btn" value="submit">
		</form>
		<br><br><div id="response"></div>

		<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
		<script src="js/homejs.js"></script>
	</body>
</html>
```

Nothing too much of interest here, the login JavaScript is exposed but it doesn't give us any sensitive data.

Ok lets just see what happens if we try to login:

![login](Images/EasyWeb/login.png)

`Okay, here is a hint for you -> eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImtleW1hc3RlciIsInBhc3N3b3JkIjoic2VjcmV0a2V5In0.oJOVw-DOUGSNjGDRWe5_kZm3MAFq_Y9YZa0QyXDbvlM`

This is something, looks a lot like a JWT token so lets chuck it in [jwt.io](https://jwt.io/) to get see it decoded(although its base64 so any tool will work)
```
{
  "username": "keymaster",
  "password": "secretkey"
}
```

There's our login credentials yay!`keymaster:secretkey`

And now logging in with these credentials gives us another hint:
`here's your next hint -> syntsvyr`. This turns out to be rot13 for `flagfile`. Visiting this on the webpage we get some fun information about flags, and in white text between paragraphs is our flag:

![flag](Images/EasyWeb/flag.png)

`HACSEC{Y0u_g0T_I7}
`
