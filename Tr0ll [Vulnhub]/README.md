# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

### Troll

First we scan the Network and find the open Ports 
We find that the ports that are open are 

 HTTP 80
 FTP 21
 SSH 22

open the webpage running on the HTTP Port
We find there is a robots.txt 
we find there is a /secret/ directory 
But unfortunately we dont find anything intresting .

Then I tried to login into ftp and i was able to find lol.pcap
which when analysed with wireshark find /sup3rsecretdirlol/

I went and opened the webpage again ...tried going into /sup3rsecretdirlol/

I was able to find user.txt and pwd.txt 
This meant i had to bruteforce the ssh with some tool like hydra  
ssh into the machine and I found a .py script that logs us out automatically  
So changed the python script to cp /root/ to /tmp so that it is accessable to every user 

and then wait for the logout script to get executed 
once we login again we have accesss to /tmp/

and then read the Proof.txt 

GG!...