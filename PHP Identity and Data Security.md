# PHP Identity and Data Security
## Jonathan LeBlanc [@jcleblanc](https://twitter.com/jcleblanc)

- book: [identity & data security for web development](http://bit.ly/iddatasecurity)
- slides: [http://bit.ly/ssphp_id_data](http://bit.ly/ssphp_id_data)

- prevent Brute force attack
	- continues attempts to guest login
	- use captcha
	- 2FA
	- key stretching
- dictorary attack
	- use a list of predetermined words/phrase to guess password
	- user salt to hash password
- rainbow tables
	- Uses recalculated password hashes to break encryption (exp. `md5`)
	- salt

### salting and peppering
- salting is better than peppering
- salt should not be static so that its uniq everytime
- sotring salts
	- store alongside the hash
- salt reuse
	- Salt should be unuque per password
- salt length
	- same size hash? 64 bit? **128 bit(standard)t**?

- bcrypt
	- Designed for password security, based on the blofish cipher, CPU & RAM intensive
- PDKDF2 (node)
 - comes from RSA laboratories, perform the HMAC (hash + key ) over a specific number of iterations
- scytpt
	- designed to mae it costly to perform large-scale hardware attack by requiring large amounts of memory

- php 7+ salt in `password_hash` depreciate salt option

### protecting user data
- ideal scenario: ssl/tls
- **organazition validation**
- extended validation

### self signed certificate (never in production)
```
openssl req 
-x509 
-nodes 
-days 365 
#new key and length
-newkey rsa:2048 
-keyout server.key 
# file name
-out server.crt
```

### Authenticate encryption
- ccm
- gcm
- kw/wkp/tkw
- includes both data and privacy authentication 

```
display all avalible modes

print_r()