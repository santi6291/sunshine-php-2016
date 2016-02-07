# Taking the web offline
## Steve Grunwell [@stevegrunwell](https://twitter.com/stevegrunwell) 

[Slides](http://stevegrunwell.github.io/taking-the-web-offline/)  
[repo](https://github.com/stevegrunwell/taking-the-web-offline)

### local DB
- LocalStorage(limited storage)
	- Simple key:value store available in modern browsers
- WebSQL(deprecated)
	- Sqlite implementation in the browser!
- IndexedDB(best modern solution)
	- Relational database implemented with JavaScript objects

### local DB API wrapper
- YDN-DB
	- Library to simplify the API, regardless of the storage engine used:

- create desktop up with [electron](http://electron.atom.io/)