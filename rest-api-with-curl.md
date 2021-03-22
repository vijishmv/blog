### GET

curl is generally invoked with just the URL. This is basically an HTTP GET request:   
```
# curl -X GET "https://httpbin.org/get"
{
  "args": {},
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-6054c318-4b322e0d4d8e0405005ff38a"
  },
  "origin": "49.207.217.136",
  "url": "https://httpbin.org/get"
}
#
```

To execute the GET method with parameter(s):  
```
# curl httpbin.org/get?user=tom
{
  "args": {
    "user": "tom"
  },
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-6054bba0-4b25d00e79a0c917097fc3e5"
  },
  "origin": "49.207.217.136",
  "url": "http://httpbin.org/get?user=tom"
}
#
```

Use double quotes when using & to include more than one parameter
```
# curl "httpbin.org/get?user=tom&type=cat&color=blue"
{
  "args": {
    "color": "blue",
    "type": "cat",
    "user": "tom"
  },
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-6054bc16-61676867533aa78913e1b29a"
  },
  "origin": "49.207.217.136",
  "url": "http://httpbin.org/get?user=tom&type=cat&color=blue"
}
#
```

### POST 

Post is used to add a new content or 'create a resource in the server'. To perform a normal (no JSON) POST request:  
```
# curl -X POST "https://httpbin.org/post" -d "user=tom&type=cat&color=blue"
{
  "args": {},
  "data": "",
  "files": {},
  "form": {
    "color": "blue",
    "type": "cat",
    "user": "tom"
  },
  "headers": {
    "Accept": "*/*",
    "Content-Length": "28",
    "Content-Type": "application/x-www-form-urlencoded",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-6054c4fd-35443c1b6382b5e861cb5df7"
  },
  "json": null,
  "origin": "49.207.217.136",
  "url": "https://httpbin.org/post"
}
#
```

To execute a POST with JSON content:  
```
# curl -X POST "https://httpbin.org/post" -H "Content-Type: application/json" -d '{"user":"tom","type":"cat","color":"blue"}'
{
  "args": {},
  "data": "{\"user\":\"tom\",\"type\":\"cat\",\"color\":\"blue\"}",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "*/*",
    "Content-Length": "42",
    "Content-Type": "application/json",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-6054c979-56ef0b105648bd321bd11ae3"
  },
  "json": {
    "color": "blue",
    "type": "cat",
    "user": "tom"
  },
  "origin": "49.207.217.136",
  "url": "https://httpbin.org/post"
}
#
Note the use of double quotes for the json elements and the single quote for the entire json content together.
```

### PUT Request 	
Put is used to update or replace a resource in the server. PUT method has to be idempotent.
```
# curl -X PUT "https://httpbin.org/put" -d "user=tom&type=cat&color=blue"
{
  "args": {},
  "data": "",
  "files": {},
  "form": {
    "color": "blue",
    "type": "cat",
    "user": "tom"
  },
  "headers": {
    "Accept": "*/*",
    "Content-Length": "28",
    "Content-Type": "application/x-www-form-urlencoded",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-60573955-5f0d3c8805e83c513339035c"
  },
  "json": null,
  "origin": "49.207.199.201",
  "url": "https://httpbin.org/put"
}
#
```

To execute a PUT with JSON content:

```
# curl -X PUT "https://httpbin.org/put" -H "Content-Type: application/json" -d '{"user":"tom","type":"cat","color":"blue"}'
{
  "args": {},
  "data": "{\"user\":\"tom\",\"type\":\"cat\",\"color\":\"blue\"}",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "*/*",
    "Content-Length": "42",
    "Content-Type": "application/json",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-605738f2-4ea3197a1232b3e60a4db6c7"
  },
  "json": {
    "color": "blue",
    "type": "cat",
    "user": "tom"
  },
  "origin": "49.207.199.201",
  "url": "https://httpbin.org/put"
}
#
```

### DELETE
This is used to delete a specific resource
```
# curl -i -X DELETE "https://httpbin.org/delete"
HTTP/2 200
date: Sun, 21 Mar 2021 13:22:27 GMT
content-type: application/json
content-length: 322
server: gunicorn/19.9.0
access-control-allow-origin: *
access-control-allow-credentials: true

{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-60574893-118da11a08da7f6e008553cb"
  },
  "json": null,
  "origin": "49.207.199.201",
  "url": "https://httpbin.org/delete"
}
#
```
Notice the use of -i to see the response headers. 

### HTTP basic authentication
```
# curl https://httpbin.org/basic-auth/tom/tompass -u tom
Enter host password for user 'tom':
{
  "authenticated": true,
  "user": "tom"
}
#
```

### Bearer authentication OR Token authentication

```
# curl -X GET "https://httpbin.org/bearer" -H "accept: application/json" -H "Authorization: a11b22c33"
#

# curl -u tom:fa1ed1en1dfbc63379e4f6c4c788 https://api.github.com/user
{
  "login": "tom",
  "id": 292,
  "node_id": "MDsdskjsiwhyMzg2",
  "avatar_url": "https://avatars.githubusercontent.com/u/292?v=4",
  "gravatar_id": "",
}
#
```

For verbose output use -v. This displays all information including TLS handshake and headers:
```
# curl -v http://httpbin.org/get
*   Trying 34.231.30.52...
* TCP_NODELAY set
* Connected to httpbin.org (34.231.30.52) port 80 (#0)
> GET /get HTTP/1.1
> Host: httpbin.org
> User-Agent: curl/7.61.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Date: Mon, 22 Mar 2021 09:13:56 GMT
< Content-Type: application/json
< Content-Length: 255
< Connection: keep-alive
< Server: gunicorn/19.9.0
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Credentials: true
<
{
  "args": {},
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.61.1",
    "X-Amzn-Trace-Id": "Root=1-60585fd4-70faaf0416197cd754a87c4b"
  },
  "origin": "49.207.199.201",
  "url": "http://httpbin.org/get"
}
* Connection #0 to host httpbin.org left intact
#
```

To output to a file
```
curl https://reqres.in/api/users > users.json
curl https://reqres.in/api/users -o users.json
```

Use https://httpbin.org/ to test basic api functionality. It even provides a docker image to run locally. 
