# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

# TryHackMe
## Web Hacking Fundamentals

GET request. Make a GET request to the web server with path /ctf/get
POST request. Make a POST request with the body “flag_please” to /ctf/post
Get a cookie. Make a GET request to /ctf/getcookie and check the cookie the server gives you
Set a cookie. Set a cookie with name “flagpls” and value “flagpls” in your devtools and make a GET request to /ctf/sendcookie


To make a get request the command used is:

    curl http://10.10.19.91:8081/ctf/get

To make a POST request the command used is:

    curl -X POST — data flag_please http://10.10.19.91:8081/ctf/post

Use the command: curl -c - ‘10.10.19.91:8081/ctf/getcookie’

    curl — cookie ‘name=value’ URL

    curl — cookie ‘flagpls=flagpls’ http://10.10.19.91:8081/ctf/sendcookie

— cookie is used to set a cookie.
