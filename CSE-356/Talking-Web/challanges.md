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

```sh

```

## babyhttp level 21

```sh

```

## babyhttp level 22

```sh

```

## babyhttp level 23

* resource : https://egeek.me/2014/08/17/sending-http-post-request-with-netcat/


```sh

```

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


```sh

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

```
## babyhttp level 29

```sh

```
## babyhttp level 24

```sh

```