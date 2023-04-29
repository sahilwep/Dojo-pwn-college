# Challanges :

#### Resources
* [Url Encoding](https://www.w3schools.com/tags/ref_urlencode.ASP)
* [Python Request](https://requests.readthedocs.io/en/latest/)
 


## babyhttp level 1

```sh
curl http://localhost:80
```

## babyhttp level 2

```sh          
rio@0xveil:~$ nc -vv localhost 80
localhost [127.0.0.1] 80 (http) open
GET / HTTP/1.0
HOST: 127.0.0.1

# result
HTTP/1.0 404 Not Found
Host: 127.0.0.1
Date: Sun, 19 Feb 2023 18:13:26 GMT
Connection: close
Content-Type: text/html; charset=UTF-8
Content-Length: 533
```

## babyhttp level 3
* In python Interactive shell type

```python
>> import requests as re
>> response = re.get("http://localhost:80")
>> print(k.text)
```

## babyhttp level 4

* We can send any custom header with `-H` in curl.

```sh
hacker@babyhttp_level4:~$ curl http://babyhttp_level4 -H "Host: 1a7ec62f61f88e42f6132c340e26204f"
```

## babyhttp level 5

* With nc sending the custom header.

```sh
hacker@babyhttp_level5:~$ nc babyhttp_level5 80 -vv
Connection to babyhttp_level5 80 port [tcp/http] succeeded!
GET / HTTP/1.0
Host: c0b4faa0b6f2ba561bc7066f731477c1

HTTP/1.1 200 OK
Server: Werkzeug/2.2.2 Python/3.8.10
Date: Sun, 19 Feb 2023 18:22:37 GMT
Content-Length: 57
Server: pwn.college
Connection: close

```

## babyhttp level 6

* With request module we can send the custom header.

```py
import requests as re

url = 'http://localhost'
headers = {'Host': '7d57292bb3804818fd35f4cdd856f474'}
response = re.get(url,headers=headers)

print(response.text)
```

## babyhttp level 7


```sh
hacker@babyhttp_level7:~$ curl http://localhost/a89a0a88682583d27f2bf599b626deba
```

## babyhttp level 8

```sh
hacker@babyhttp_level8:~$ nc localhost 80
GET /626c3c42d591698a45debb1285a1d87a HTTP/1.0
Host: localhost

HTTP/1.1 200 OK
Server: Werkzeug/2.2.2 Python/3.8.10
Date: Sun, 19 Feb 2023 18:43:48 GMT
Content-Length: 57
Server: pwn.college
Connection: close
```

## babyhttp level 9

```py
import requests as re

url = 'http://localhost/759b2301e8a14071872e8bd6eea03494'
headers = {'Host': '7d57292bb3804818fd35f4cdd856f474'}
response = re.get(url,headers=headers)

print(response.text)
```

## babyhttp level 10

```sh
hacker@babyhttp_level10:~$ curl http://babyhttp_level10/path
Incorrect path: value `/path`, should be `/bc907756 b20fb5c3/e5b896df 1d51848b`
hacker@babyhttp_level10:~$ curl http://babyhttp_level10/bc907756%20b20fb5c3/e5b896df%201d51848b
# answer
```

## babyhttp level 11

```sh
hacker@babyhttp_level11:~$ nc localhost 80
GET /path HTTP/1.0
Host: asdlf.asdf

HTTP/1.1 400 BAD REQUEST
Server: Werkzeug/2.2.2 Python/3.8.10
Date: Sun, 19 Feb 2023 18:56:17 GMT
Content-Length: 80
Server: pwn.college
Connection: close

Incorrect path: value `/path`, should be `/efafc220 4e7b6fc9/522a4f2d 2abf8788`
^C
hacker@babyhttp_level11:~$ nc localhost 80
GET /efafc220%204e7b6fc9/522a4f2d%202abf8788
Host: asdf

# answer
```

## babyhttp level 12
* url encoding `%20` for space
```py
import requests as re

url = 'http://localhost/f7dd8e2c%20a76d251b/769ee7a0%201ef45023'
headers = {'Host': '7d57292bb3804818fd35f4cdd856f474'}
response = re.get(url,headers=headers)

print(response.text)
```

## babyhttp level 13

* Passing arguments with curl.

```sh
hacker@babyhttp_level13:~$ curl "http://localhost"
Incorrect arg `a`: value `None`, should be `0afa2225fe9449c0afbcca1bcf9f8eb3`
hacker@babyhttp_level13:~$ curl "http://localhost/?a=0afa2225fe9449c0afbcca1bcf9f8eb3"
# answer
```

## babyhttp level 14

* Arguments with `nc`
```sh
hacker@babyhttp_level14:~$ nc localhost 80 -vv
Connection to localhost 80 port [tcp/http] succeeded!
GET /?a=cbf2e7e52c39f419cf98d7783ddf372b HTTP/1.0
Host: hey.hey

HTTP/1.1 200 OK
Server: Werkzeug/2.2.2 Python/3.8.10
Date: Sun, 19 Feb 2023 19:13:15 GMT
Content-Length: 57
Server: pwn.college
Connection: close

# answer
```

## babyhttp level 15
* With python script.

```sh
import requests as re

url = 'http://localhost/?a=3b77fcab764bcad91f77bfc016ba273f'
headers = {'Host': '7d57292bb3804818fd35f4cdd856f474'}
response = re.get(url,headers=headers)

print(response.text)
```

## babyhttp level 16

* Request multiple arguments using curl.
* 
```sh
hacker@babyhttp_level16:~$ curl "http://localhost/?a=2c84971c920baa5aad51ea8b6ec22ddb&b=c1b36da8%2097451f1b%26c9b0f864%23be46df89"
```

## babyhttp level 17

* Multiple argument with url encoding using nc.
```sh
hacker@babyhttp_level17:~$ nc localhost 80 -vv
Connection to localhost 80 port [tcp/http] succeeded!
GET /?a=6fc44c17fb9708ea200487eed873ee34&b=58390281%20c780a30f%26af7a1bcd%237abed5d0
Host: asdf

```

## babyhttp level 18

```py
import requests as re

url = 'http://localhost/?a=2f6e0b74dc6ec521c4480c3a75c2d3b9&b=4cea8b0e%2093b0802c%26097d3330%233a7922e5'
headers = {'Host': '7d57292bb3804818fd35f4cdd856f474'}
response = re.get(url,headers=headers)

print(response.text)

```

## babyhttp level 19

* Pass data with curl.
```sh
hacker@babyhttp_level19:~$ curl http://localhost -d "a=886fa04846828cd7dc00918e0de1d3d1"
```

## babyhttp level 20

* Include form data in an HTTP request using nc
* adding multiple parameter will give the flag.

> req.txt
```palin
hacker@talking-web-level-20:~$ cat req.txt 
GET / HTTP/1.1
Host: 127.0.0.1
Connection: keep-alive
Content-Length: 35
Content-Type: application/x-www-form-urlencoded
User-Agent: curl/7.2

a=9a75236d458278bffcf68048defb983c&b=calsd
```
> challange
```sh
hacker@talking-web-level-20:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 400 BAD REQUEST
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 17:41:34 GMT
Content-Length: 108
Server: pwn.college
Connection: close

Incorrect form `a`: value `9a75236d458278bffcf68048defb983c
`, should be `9a75236d458278bffcf68048defb983c`

hacker@talking-web-level-20:~$ nano req.txt 

hacker@talking-web-level-20:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 17:43:31 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{flag}

```

## babyhttp level 21

* Include form data in an HTTP request using python 

```py
import requests as re

url = 'http://localhost/'
headers = {'Content-type': 'application/json'}
data = {"a": "c61b7eb3605bc2a2fdbbcac920bdd414"}
response = re.post(url , data=data )
print(response.text)
```
## babyhttp level 22

* Include form data with multiple fields in an HTTP request using curl

```sh
hacker@talking-web-level-22:~$ curl http://localhost -X POST  -d "a=asdf"
Incorrect form `a`: value `asdf`, should be `88869684b19951606208beea283619a7`

hacker@talking-web-level-22:~$ curl http://localhost -X POST  -d "a=88869684b19951606208beea283619a7"
Incorrect form `b`: value `None`, should be `7b36009a 7fba17d1&59e951b7#08e564f2`
#  here I use url encoding for # & and blank space
hacker@talking-web-level-22:~$ curl http://localhost -X POST  -d "a=88869684b19951606208beea283619a7&b=7b36009a%207fba17d1%2659e951b7%2308e564f2"
pwn.college{flag-here}
```

## babyhttp level 23
* Include form data with multiple fields in an HTTP request using nc
* doning we need to add extra data at end to get the flag.
* we need to aware about content length.

```plain
GET / HTTP/1.1
Host: 127.0.0.1
Connection: keep-alive
Content-Length: 87
Content-Type: application/x-www-form-urlencoded
User-Agent: curl/7.2

a=381bd8c7b22ab5e06388d7a7fb1b8a74&b=61de1d1f%20ddd96cfc%26cb138910%235d861478&c=sahil
```

```sh
hacker@talking-web-level-23:~$ nano req.txt 

hacker@talking-web-level-23:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 18:08:59 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{falg-here}
```
* [resource](https://arpitbhayani.me/blogs/making-http-requests-using-netcat)

## babyhttp level 24

* Include form data with multiple fields in an HTTP request using python

```python
import requests as re
url = 'http://localhost/?a=c61b7eb3605bc2a2fdbbcac920bdd414'
headers = {'Host': '7d57292bb3804818fd35f4cdd856f474'}
payload = {
        "a": "e0e6b48903dd59d7c0f77f887431df19",
        "b": "80d8a13c 9204c572&bd6c187a#48797890"
}

response = re.get(url,data= payload,headers=headers)
print(response.text)
```
* for passing multiple data we use dictionary & inside there is no need for url encoding....

## babyhttp level 25
* Include json data in an HTTP request using curl
* We use `-H` for Custom header..
* We use json format to pass in `-d`

> Example :
```sh
curl -X POST [URL]
     -H "Content-Type: application/json"
     -H "Accept: application/json" 
     -d '{"Id": 7,"Customer":"Leo"}'
```
> Flag
```sh
curl http://localhost -i -H "Content-type: application/json" -d '{"a": "9d3c6f900acc66092fb1482d7dffc982"}'
HTTP/1.1 200 OK
Server: Werkzeug/2.2.2 Python/3.8.10
Date: Tue, 21 Feb 2023 07:07:27 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{_here-flag_}

```


## babyhttp level 26

* Include json data in an HTTP request using nc
* We need to check for the correct content length..

```plain
GET / HTTP/1.1
Host: 127.0.0.1
Connection: keep-alive
Content-Length: 42
Content-Type: application/json
User-Agent: curl/7.2.

{"a": "25613d9ab74f71611ba6fec313b1c2ab"}
```

```sh
hacker@talking-web-level-26:~$ cat req.txt 
GET / HTTP/1.1
Host: 127.0.0.1
Connection: keep-alive
Content-Length: 15
Content-Type: application/json
User-Agent: curl/7.2.

{"a": "value"}

hacker@talking-web-level-26:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 400 BAD REQUEST
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 18:16:50 GMT
Content-Length: 80
Server: pwn.college
Connection: close

Incorrect json `a`: value `value`, should be `25613d9ab74f71611ba6fec313b1c2ab`

hacker@talking-web-level-26:~$ nano req.txt 

hacker@talking-web-level-26:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 18:17:40 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{flag-here}
```

## babyhttp level 27

* Include json data in an HTTP request using python

```sh
import requests as re

url = 'http://localhost/'
headers = {'Content-type': 'application/json'}

response = re.post(url,json={ "a": "51d97df3860e539198645151bac2b128" } ,headers=headers)

print(response.text)
```

## babyhttp level 28

* Include complex json data in an HTTP request using curl

```sh
hacker@talking-web-level-28:~$ curl http://localhost -H "Content-type: application/json" -d '{"a": "b312602cde86740e565ba426bb397756","b": {"c": "eb15d203", "d": ["500141d9", "asdf"]}}'
Incorrect json `b`: value `{'c': 'eb15d203', 'd': ['500141d9', 'asdf']}`, should be `{'c': 'eb15d203', 'd': ['500141d9', '64c77913 1ee662c8&e05df20d#c04ca65d']}`


hacker@talking-web-level-28:~$ curl http://localhost -H "Content-type: application/json" -d '{"a": "b312602cde86740e565ba426bb397756","b": {"c": "eb15d203", "d": ["500141d9", "64c77913 1ee662c8&e05df20d#c04ca65d"]}}'
pwn.college{flag_here}
```
## babyhttp level 29

* Include complex json data in an HTTP request using nc

```plain
GET / HTTP/1.1 
Host: 127.0.0.1    
Connection: keep-alive
Content-Length: 124
Content-Type: application/json
session=eyJzdGF0ZSI6MX0.Y_tXwA.-QrYmOJH_WJwbvjVlm3V8eVA3B0
User-Agent: curl/7.2

{"a": "d5408c3572f4fa2b96b468adee54ffcc", "b": {"c": "e125eb01", "d": ["fe5a38ae", "4f656b5d 9d59575d&05e97632#df66cafb"]}}
```
hacker@talking-web-level-29:~$ cat req.txt  | nc localhost 80 
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Sun, 26 Feb 2023 13:13:55 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{flag-here}
```sh
Not yet done!
```

## babyhttp level 30

* Include complex json data in an HTTP request using python
```sh
url = 'http://localhost/'
headers = {'Content-type': 'application/json'}
json_file = {
                "a": "1d65d77c9b9ab358e71f955fbc014f5e",
                "b": {
                        "c": "9d684187",
                        "d": [
                                '313faf2d', 
                                '36c82b6d 1ad5ad68&2744100f#091da8ec'
     ]
  }
}
response = re.post(url,json = json_file , headers = headers )
print(response.text)
```

## babyhttp level 31

* Follow an HTTP redirect from HTTP response using curl

```sh
hacker@talking-web-level-31:~$ curl http://localhost -L
pwn.college{-flag-here-}
```


## babyhttp level 32
* Follow an HTTP redirect from HTTP response using nc
* After fails we paste the location in req.txt
> req.txt
```plain
GET /904dc4a2a09e2b0676d528e04e5fce6f HTTP/1.1
Host: 127.0.0.1
Connection: keep-alive
Content-Length: 43
Accept: application/json, text/javascript, */*; q=0.01
Cookie: cookie=1edf04ac5e3cd34b9716ceac6b943a28
X-Requested-With: XMLHttpRequest
User-Agent: curl/7.2
Content-Type: application/json

[{"a":"thei9023m","args":{"--json":true}}]
```

> challange
```sh
hacker@talking-web-level-32:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 302 FOUND
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 17:09:25 GMT
Content-Length: 253
Location: /904dc4a2a09e2b0676d528e04e5fce6f
Server: pwn.college
Connection: close

<!doctype html>
<html lang=en>
<title>Redirecting...</title>
<h1>Redirecting...</h1>
<p>You should be redirected automatically to the target URL: <a href="/904dc4a2a09e2b0676d528e04e5fce6f">/904dc4a2a09e2b0676d528e04e5fce6f</a>. If not, click the link.

hacker@talking-web-level-32:~$ nano req.txt 

hacker@talking-web-level-32:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 17:11:50 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{flag-here}
```


## babyhttp level 33

* Follow an HTTP redirect from HTTP response using python.

```python
import requests as re

url = 'http://localhost/'
headers = {'Content-type': 'application/json'}
json_file = {
                "a": "1d65d77c9b9ab358e71f955fbc014f5e",
                "b": {
                        "c": "9d684187",
                        "d": [
                                '313faf2d', 
                                '36c82b6d 1ad5ad68&2744100f#091da8ec'
     ]
  }
}
response = re.post(url,json = json_file , headers = headers )
print(response.text)
```

## babyhttp level 34

* Include a cookie from HTTP response using curl

* In first attempt it show the redirection with set cookie this... so i used it..
```sh
hacker@talking-web-level-34:~$ curl -i -L  http://localhost -b "name=value" 
HTTP/1.1 302 FOUND
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 16:55:33 GMT
Content-Length: 189
Location: /
Set-Cookie: cookie=3dc44b92983ffffaab9acd188aa904ed; Path=/
Server: pwn.college
Connection: close


hacker@talking-web-level-34:~$ curl -i -L  http://localhost -b "cookie=3dc44b92983ffffaab9acd188aa904ed" 
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 16:56:25 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{flag-here}
```


## babyhttp level 35

* Include a cookie from HTTP response using nc

> req.txt
```plain
GET / HTTP/1.1
Host: 127.0.0.1
Connection: keep-alive
Content-Length: 43
Accept: application/json, text/javascript, */*; q=0.01
Cookie: cookie=1edf04ac5e3cd34b9716ceac6b943a28
X-Requested-With: XMLHttpRequest
User-Agent: curl/7.2
Content-Type: application/json

[{"a":"thei9023m","args":{"--json":true}}]
```
> challange
```sh
hacker@talking-web-level-35:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 302 FOUND
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 17:02:18 GMT
Content-Length: 189
Location: /
Set-Cookie: cookie=1edf04ac5e3cd34b9716ceac6b943a28; Path=/
Server: pwn.college
Connection: close

<!doctype html>
<html lang=en>
<title>Redirecting...</title>
<h1>Redirecting...</h1>
<p>You should be redirected automatically to the target URL: <a href="/">/</a>. If not, click the link.

hacker@talking-web-level-35:~$ nano req.txt 

hacker@talking-web-level-35:~$ cat req.txt  | nc localhost 80 -v
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Fri, 24 Feb 2023 17:04:28 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{flag-here}
```

## babyhttp level 36


```py
import requests as re

url = 'http://localhost/'
headers = {'Content-type': 'application/json'}
data = {"name": "key"}
json_file = {
                "a": "1d65d77c9b9ab358e71f955fbc014f5e",
                "b": {
                        "c": "9d684187",
                        "d": [
                                '313faf2d',                                                                                          
                                '36c82b6d 1ad5ad68&2744100f#091da8ec'
     ]
  }
}
response = re.post(url,json = json_file ,cookies=data,  headers = headers )
print(response.text)
```

## babyhttp level 37

* Make multiple requests in response to stateful HTTP responses using curl

* we use `--cookie-jar file_name` to write cookie to file after every operation.
```sh
hacker@talking-web-level-37:~$ curl http://localhost -v --cookie-jar file -L
*   Trying 127.0.0.1:80...
* TCP_NODELAY set
* Connected to localhost (127.0.0.1) port 80 (#0)
> GET / HTTP/1.1
> Host: localhost
> User-Agent: curl/7.68.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 302 FOUND
< Server: Werkzeug/2.2.3 Python/3.8.10
< Date: Sun, 26 Feb 2023 15:57:02 GMT
< Content-Length: 9
< Location: /
< Server: pwn.college
< Vary: Cookie
* Added cookie session="eyJzdGF0ZSI6MX0.Y_uBTg.Vh5hzA2akzL0ttNU4qNplqhk2Ts" for domain localhost, path /, expire 0
< Set-Cookie: session=eyJzdGF0ZSI6MX0.Y_uBTg.Vh5hzA2akzL0ttNU4qNplqhk2Ts; HttpOnly; Path=/
< Connection: close
< 
* Closing connection 0
* Issue another request to this URL: 'http://localhost/'
* Hostname localhost was found in DNS cache
*   Trying 127.0.0.1:80...
* TCP_NODELAY set
* Connected to localhost (127.0.0.1) port 80 (#1)
> GET / HTTP/1.1
> Host: localhost
> User-Agent: curl/7.68.0
> Accept: */*
> Cookie: session=eyJzdGF0ZSI6MX0.Y_uBTg.Vh5hzA2akzL0ttNU4qNplqhk2Ts
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 302 FOUND
< Server: Werkzeug/2.2.3 Python/3.8.10
< Date: Sun, 26 Feb 2023 15:57:02 GMT
< Content-Length: 9
< Location: /
< Server: pwn.college
< Vary: Cookie
* Replaced cookie session="eyJzdGF0ZSI6Mn0.Y_uBTg.dhiAYc_rzDZkAyxL7gafCrNR2pA" for domain localhost, path /, expire 0
< Set-Cookie: session=eyJzdGF0ZSI6Mn0.Y_uBTg.dhiAYc_rzDZkAyxL7gafCrNR2pA; HttpOnly; Path=/
< Connection: close
< 
* Closing connection 1
* Issue another request to this URL: 'http://localhost/'
* Hostname localhost was found in DNS cache
*   Trying 127.0.0.1:80...
* TCP_NODELAY set
* Connected to localhost (127.0.0.1) port 80 (#2)
> GET / HTTP/1.1
> Host: localhost
> User-Agent: curl/7.68.0
> Accept: */*
> Cookie: session=eyJzdGF0ZSI6Mn0.Y_uBTg.dhiAYc_rzDZkAyxL7gafCrNR2pA
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 302 FOUND
< Server: Werkzeug/2.2.3 Python/3.8.10
< Date: Sun, 26 Feb 2023 15:57:02 GMT
< Content-Length: 9
< Location: /
< Server: pwn.college
< Vary: Cookie
* Replaced cookie session="eyJzdGF0ZSI6M30.Y_uBTg.5ez9-b45j4rb_i7WH8RhjzttMKc" for domain localhost, path /, expire 0
< Set-Cookie: session=eyJzdGF0ZSI6M30.Y_uBTg.5ez9-b45j4rb_i7WH8RhjzttMKc; HttpOnly; Path=/
< Connection: close
< 
* Closing connection 2
* Issue another request to this URL: 'http://localhost/'
* Hostname localhost was found in DNS cache
*   Trying 127.0.0.1:80...
* TCP_NODELAY set
* Connected to localhost (127.0.0.1) port 80 (#3)
> GET / HTTP/1.1
> Host: localhost
> User-Agent: curl/7.68.0
> Accept: */*
> Cookie: session=eyJzdGF0ZSI6M30.Y_uBTg.5ez9-b45j4rb_i7WH8RhjzttMKc
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: Werkzeug/2.2.3 Python/3.8.10
< Date: Sun, 26 Feb 2023 15:57:02 GMT
< Content-Length: 57
< Server: pwn.college
< Vary: Cookie
* Replaced cookie session="eyJzdGF0ZSI6NH0.Y_uBTg.VJyQ2_obWTgBa3_5wRC1fHZZp68" for domain localhost, path /, expire 0
< Set-Cookie: session=eyJzdGF0ZSI6NH0.Y_uBTg.VJyQ2_obWTgBa3_5wRC1fHZZp68; HttpOnly; Path=/
< Connection: close
< 
pwn.college{falg-here}
* Closing connection 3
```
## babyhttp level 38

* Make multiple requests in response to stateful HTTP responses using nc

* when i first request with any random cookie, the server send me the cookie file, then i set the cookie into header and again request with new cookie, again i got new cookie .. then again i set this cookie into headers.. then again I get new one.. repeating this process until we got the flag.

> req.txt

```plain
GET / HTTP/1.1
Host: 127.0.0.1
Connection: keep-alive
Content-Length: 42
Cookie: session=eyJzdGF0ZSI6M30.Y_zgzw.wC6M10J15SSsvX0v8ElhYLhRzLA
Content-Type: application/json
User-Agent: curl/7.2

{"a": "d5408c3572f4fa2b96b468adee54ffcc"}
```

> Challanges
```sh
┌──(rio💀0xveil)-[~]
└─$ ssh -i ~/tools/dojo/key hacker@dojo.pwn.college
Connected!                                                                        
hacker@talking-web-level-38:~$ cat req.txt  | nc localhost 80 -v 
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 302 FOUND
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Mon, 27 Feb 2023 16:56:31 GMT
Content-Length: 9
Location: /
Server: pwn.college
Vary: Cookie
Set-Cookie: session=eyJzdGF0ZSI6Mn0.Y_zgvw.1bdmk_lyZ9UrXczQ1ibYG_fMSNE; HttpOnly; Path=/
Connection: close

state: 2
hacker@talking-web-level-38:~$ cat req.txt  | nc localhost 80 -v 
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 302 FOUND
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Mon, 27 Feb 2023 16:56:47 GMT
Content-Length: 9
Location: /
Server: pwn.college
Vary: Cookie
Set-Cookie: session=eyJzdGF0ZSI6M30.Y_zgzw.wC6M10J15SSsvX0v8ElhYLhRzLA; HttpOnly; Path=/
Connection: close

state: 3
hacker@talking-web-level-38:~$ cat req.txt  | nc localhost 80 -v 
Connection to localhost 80 port [tcp/http] succeeded!
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Mon, 27 Feb 2023 16:57:06 GMT
Content-Length: 57
Server: pwn.college
Vary: Cookie
Set-Cookie: session=eyJzdGF0ZSI6NH0.Y_zg4g.uqoLicGHLakMF1SPkocN6DjqtnQ; HttpOnly; Path=/
Connection: close

pwn.college{falg-here}
```

## babyhttp level 39

* Make multiple requests in response to stateful HTTP responses using python

```py
import requests as re

url = 'http://localhost/'
headers = {'Content-type': 'application/json'}
data = {"a": "c61b7eb3605bc2a2fdbbcac920bdd414"}
response = re.post(url , data=data )
print(response.text)

hacker@talking-web-level-39:~$ python script.py 
pwn.college{falg-here}

```
