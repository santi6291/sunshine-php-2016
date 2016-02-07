# Give Me a REST!
## Amanda Folson [@AmbassadorAwsum](https://twitter.com/AmbassadorAwsum)

### REST

### design

- immutable blueprint
- contract between you and users
- Share
	- the worst feedback is the feedback k you don't hear
- account for existing architecture
- changes should provide actual value not precede potential value
- design for uniformity

### spec tools
- API blueprint
- swagger

### POST
- returns 201 created

### PUT
- generally updates a resources 
- overwrites existing object with new one

### Patch
- returns 200 ok on successful update

### Replying
- 200 ok
- 201 created
- 204 no content
- 304 not modified
- 5xx we screwed up, 
- 400 not found

### hateoas
- hypermedia as the enfine of the applications tate
- hypertext links to other resources
	- every object has actions to perfirm

### hypermedia spec
- wishful thinking
- there are no standers for this
- JSON api? custom? HAL?
- HAL/JSON API are good stating points with wide adaptation

### when to version
- backwards uncompatible changes
	- creating new data model
- when api docent meet users needs
- not when you add new resources or data fields

### versioning in URI
- http://myapiuri.com/v1/stuff
- relative path can't always be hypermedia friven

### version in content-type
- content-type: application/son_v1

### Version in custom header
- required great documentation 
- no standards
- confusing for users for users who aren't expecting it

### caching
- cache on client end

### Authentication
- kill basic Auth
	- keep username/passwords safe
- OAuth
	- require users to explicitly authorize an app
	- Tricky for some people to implement
	- restrict auth to https endpoint
	- restrict domains allowed to auth
	- MITM attack, make sure users store tokens well

### Security

- 	treat users as hostile
-  don't rely on single method
-  permission -based api keys/uac
-  DNSBL
-  content length/depth limits
-  sql injection
-  rate limit/throttling

### prototyping
- Laravel/Lumen, flask, rails, mojolicious
	- RESTful http routing
	- Zero to api in 1hr
- Specs
	- Apiary, mockable, RAML
- Chrome RESt API client, Postman, jsfiddle

### SDK's
- log in to view api docks