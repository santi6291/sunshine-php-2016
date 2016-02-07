# HTTP/2 The (not so) new language of the web
## Adrian Cardenas [@aramonc](https://twitter.com/aramonc)

- [Slides](http://www.slideshare.net/aramonc/http2-57936021)
- SPDY: basis for http/2

### Binary Protocol Features
- Binay framing
- streams
- request &response multiplex
- stream prioritization
- single connection

### The final HTTP/2 RFC(s)
- HTTP2-RFC7540
	- describe binary protocal
- HPACK - header compression for http2-RFC7541
- published in may 2015

### Implementation
- Apache 2.4.17
- NGINX 1.9.5
- CURL7.38.0
- [browser support](http://caniuse.com/#search=http2)

### Binary framing
- similar to TCP packets
- frames contain distinct data (header, payload, etc)frames are indexed
- fixed length

### Streams
- bidirectional flow of bytes within a connection
- may carry one or more messages
- Single TCP connection can carry several streams
- have identifiers
- can be prioritized

### Capable of multiplexing
- frames in different streams can be interleaved
- Solves head-of-line blocking 
	- can download multiple things 
	- solves waiting for file to be done downloading to get next file

### header compression
- original SPDY compression was vulnerable
- HPACK used in http/2
- HPACK uses 2 compression techniques
	- [Huffman compression](https://www.wikiwand.com/en/Huffman_coding)
	- Client & server must keep indexed list of previously seen headers

### Server push
- server knows content needed
- server sends a PUSH_PROMISE frame
- client can decide to accept frame or reset it
- **currenctly still experimental**
- recommneded for

### TLS Only
- Not mandated by the standerrd
- Chome & firebox stated they will not support without tls
- performance issues balanced in single connection senartio
- [https://letsencrypt.org/](https://letsencrypt.org/)
	- **free ssl certificate for low traffic website**

### connection updagrede
- ALPN during TLS hand-shake
	- recommended
- Connection & Upgrade header

### DoS Vectors
- Single connection reduces many vector
- tcp is still point of failure
- HPACK & required buffering can be memory intensive
- HPACK cab be used to increase payload
- Header frames cannot be interrupted

### Waht does this mean for you?
- Increased performance
	- conservative measures of 5% to 15%
	- decreased resource use
		- one connection for one customer
	- new tools for debugging & monitoring
	- happier customers 
	- tiem to switche

### Transition plan
- Know you application as it is
- which strategy is best fit your customer
- priority 
	- internal backend API (smaller payloads)
	- public API's
	- [CDNs](http://www.wikiwand.com/en/Content_delivery_network)
	- front end app
	- load balancers & other proxies\
- Implmentation
	- sit and wait
	- adopt http/2 completely
	- hybrid approach
- Talk of google will push up search result for http/2 

### Benchmark
- Load inpacp comparison tool 
	- http://http2.loadimpact.com/entry/