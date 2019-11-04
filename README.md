# Technical Support Engineer Assesment
## Steps to Submit
1. Create an ssh key on your machine if you do not have one
1. Send us your ssh public key
1. Create a GitHub Account
1. Git Clone this repository to your local machine
1. Remove the current origin remote (git remote remove origin)
1. Create a new repository under your GitHub account (do NOT fork this repository)
1. Follow the instructions to push an existing repository from the command line...
1. Add answers to this Document (either to this document or create different for each question), commit your answers to the branch
1. Push your answers to your personal remote origin in your git account
1. Send a notification to us with a link to your repository
If any of the steps above is unclear, please try GitHub user guides.
The method of submission is part of the test (usage of Git)

## Questions
1. A customer has reached out to us that he cannot access our platform running on 45.33.22.50. Customer's complain is as follows:
- "Hello, It seems i cannot access http://45.33.22.50/test1"

2. A customer has reached out to us that he cannot access our platform running on 45.33.22.50. Customer's complain is as follows:
- "Hello, It seems i cannot access http://45.33.22.50:444/test2. When i access it seems that nothing happens"

## To Do
- For both above questions what are the actions you will take to evaluate customers request.

* Check if I can enter or if I don't have access either.
* Validate what is the error message, normally it could be 404 or 500.
* What is the script supposed to do?
* What is it actually doing?
* Ask questions to customer to get more detail of the fault.

- Include questions we may need to ask to get additional information to ensure the best customer support.

* At what time did the fault occur?
* Do you know if anyone else has the same fault?
* When was the last time it worked correctly?
* Was there any recent change on your system or some application recently installed?
* What browser are you using, have you tried any other? 






- Add an explanation why you ask each question (what do you expect to receive back.

The first step before starting a problem analysis is to identify if it is an isolated fault or if it is a massive problem, so it is important to collect information regarding the end user, date and time of the problem, error message, recent changes in the equipment, etc ... 

- Additionaly you need to ssh to the machine and troubleshoot the above scenarios.

1.- Check if nginx is running:

user2@localhost:~$ service nginx status
  nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2019-10-30 13:59:50 UTC; 5 days ago
     Docs: man:nginx(8)
 Main PID: 16203 (nginx)
    Tasks: 2 (limit: 1109)
   CGroup: /system.slice/nginx.service
           ??16203 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
           ??24992 nginx: worker process

3.- Check path for errors:

user2@localhost:~$ nginx -V
nginx version: nginx/1.14.0 (Ubuntu)
built with OpenSSL 1.1.1  11 Sep 2018
TLS SNI support enabled
configure arguments: --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-DUghaW/nginx-1.14.0=. -fstack-protector-strong -Wformat -Werror=format-security -

fPIC -Wdate-time -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' --prefix=/usr/share/nginx --conf-

path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log



3.- Review the error log for nginx:

user2@localhost:/var/log/nginx$ more error.log
2019/11/04 14:10:02 [error] 24992#24992: *120 directory index of "/var/www/html/" is forbidden, client: 161.117.199.105, server: , request: "GET / HTTP/1.1", host: "45.33.22.50:443"
2019/11/04 14:10:03 [error] 24992#24992: *122 directory index of "/var/www/html/" is forbidden, client: 161.117.199.105, server: , request: "GET / HTTP/1.1", host: "45.33.22.50:443"
2019/11/04 14:10:04 [error] 24992#24992: *123 directory index of "/var/www/html/" is forbidden, client: 161.117.199.105, server: , request: "POST / HTTP/1.1", host: "45.33.22.50:443"
2019/11/04 14:10:04 [error] 24992#24992: *124 directory index of "/var/www/html/" is forbidden, client: 161.117.199.105, server: , request: "GET / HTTP/1.1", host: "www.psiphon3.com"

5.- Check information about ports:

user2@localhost:/etc/nginx/sites-available$ ls -lrt
total 8
-rw-r--r-- 1 root root 136 Oct 31 09:57 default
-rw-r--r-- 1 root root 135 Oct 31 10:00 test2
user2@localhost:/etc/nginx/sites-available$ more default
server {
  listen 443  default_server;
  location /test1 {
        proxy_pass http://localhost:5000/test1;
  }

  root /var/www/html;
}
user2@localhost:/etc/nginx/sites-available$ more test2
server {
  listen 444 default_server;
  location /test2 {
        proxy_pass http://localhost:5000/test2;
  }

  root /var/www/html;
}
user2@localhost:/etc/nginx/sites-available$

6.- Make tests:

user2@localhost:/var/log/nginx$ curl -i http://45.33.22.50:443/test1
HTTP/1.1 200 OK
Server: nginx/1.14.0 (Ubuntu)
Date: Mon, 04 Nov 2019 21:25:04 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 16
Connection: keep-alive


Completed Test 1user2@localhost:/var/log/nginx$ curl -i http://45.33.22.50:444/test2
curl: (7) Failed to connect to 45.33.22.50 port 444: Connection refused
user2@localhost:/var/log/nginx$



7.- Correct URL is:

http://45.33.22.50:443/test1"

8.- For the second URL port 444 can be blocked by firewall, 


- Make sure you list in detail what are the steps you followed to identify and resolve the problem.

1.- Get more details about the issue.
2.- Try to replicate the fault.
3.- Analyze error messages on the screen (webpage).
4.- Analyze logs on the server.
5.- If the service is down, start it and report the event to 
    The development team.
6.- If the service is up report to the development team.
7.- Validate if problem has been solved.
8.- Document the fault to get the root cause of the problem


Hint: The platform runs on nginx and python
