# Web Security and You
## Eli White [@EliW](https://twitter.com/EliW)

- [Open web Application security project](http://owasp.org/)
- [slides](http://eliw.com/wp-content/uploads/2016/02/sunshine.security.pdf)

### password hashing
- don't not user MD5 alone
	- highly vulnerable to `rainbow tables`
- Always 1 way hash
- Don't' even use `SHA-1` or `SHA-512`
- The longer your hash takes to run the longer it takes for someone to crack it

### php 5.5
- built in password hash `password_hash` and `password_verify`
- use `PASSWORD_DEFAULT` will use the latest algorithm for hashing
- highest the `[cost => 12]` the longer it takes to generate hash
	- default 10
- [php Password Hashing](http://php.net/password)

### Attack vectors
- SQL injection
	- use `prepare` statements and `execute`
		- process sql query and then pass text avoiding modification of statment
	- or
	- escape parameter
- Command Injection: the user being able to inject ode into a command line
- Unchecked file uploads: the user being allowed to upload an executable file
	- [escapeshellarg()](http://php.net/manual/en/function.escapeshellarg.php)
- code injection: User being able to directly inject code (DON'T USE EVAL)
	- eval is one character different from evil

### Session Hijacking
- one user 'becoming' another user
- Sessions fixation (don't user )
	- user uses someone else session to hijack someone else sessions
- do not use session name by `PHPSESSID`
- solution

```
session_start();
if( $user->login( $_POST['user'], $_POST['pass'] ) ){
	session_regenerate_id(TRUE)
}
```

and

```
session_start();
$user->logout();
session_regenerate_if(TRUE);
```

### Session anti-hijack measures 
- Use SSL
- check initial request and check second request for similar patterns
- use `user agent` to generate token 
	- request session id and token to prevent hijack session
- add `time stamp` and generate hash from it

### XSS (cross site scripting)

- reflected XSS
	- security hole `<p> thank you <?= $_POST['name']>`
	- the solution escape string, check for value type
		- html: `$name = htmlentities($_post['firstname], ENT_QUOTES, 'UTF-8', FALSE)`
		- JS: `$name= str_replace(array("\t\n", "\r", "\n")), array("\n", "\n", "\\\n")`
- Stored XXS
	- Stores data to display later
	- change username to black of script and when viewing user script will execute
	- solution: escape value
- DOM XSS
	- js: dont user html if only want text to be rendered
	- [jquery-encoder](https://github.com/chrisisbeef/jquery-encoder)
	- always round trip to the server

### CSRF (Cross site request forgery)

- a user having the ability to force or force a request on behalf of another user
- generate token per form submission save to session
- check for token in post
- example: invisible iframe making you click on a button that seems to do nothing but is executing on iframe
- Use specific header to disallow site framing
	- `header(X-frame-Optons: DENY);`
	- `header(X-frame-Optons: SAMEORIGIN);`

### Notes

- Kepp your stack patched
- DDOS (good luck)
	- rely on firewall features and hosting
	- Hire a good ops team
- Man in the middle
	- SSL best solution