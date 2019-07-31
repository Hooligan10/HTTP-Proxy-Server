# Proxy Server
An HTTP proxy server implemented via python socket programming with caching

## Description
- `proxy.py` is the main proxy file
- Proxy runs on some specific ports.
- Client keeps asking any file from server by GET method using curl request.
- Server listens to specified port and returns any file as asked
- Proxy works as middleman between the server and client and it does the caching.
- Only GET requests are handled via this process.

## Features
- Receives the request from client and pass it to the server after necessary parsing
- Threaded proxy server is able to handle many requests at the same time
- Separate Cache folder is created for storing cached messages.
- If one file is requested above the threshold number of times in certain time period, then proxy server caches that request. The threshold number and time limit can be set by changing global constants in *proxy.py* file
- Cache has limited size, so if the cache is full and proxy wants to store another response then it removes the least recently asked cached response. Cache limit can be set by setting up the constant in *proxy.py* file.
- Proper error handling is done for showing error messages if file is not present at the server.
- In our implementation, we are storing error message in cache also. 

## Running ->

#### Proxy
- Run proxy as-
	`python proxy.py`
	It will run proxy on port 20000

#### Server
- run server in *server/* directory

- `python server.py 19991` to run server on port 19991

#### Client
- curl request can be sent as client request and get the response.  
`curl --request GET --proxy 127.0.0.1:20000 --local-port 20002 127.0.0.1:19991/1.txt`  
this request will ask 1.txt file from server 127.0.0.1/19991 by GET request via proxy 127.0.0.1/20000


- see the changes in cache directory.



