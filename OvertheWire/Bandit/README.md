# Welcome to Neouchiha's Blog

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)


# OvertheWire
## Bandit
### Level 0->1:
Use 
```cat readme``` 
### Level 1->2:
Use 
```cat  ./-```
### Level 2->3:
Use 
```cat spaces\ in\ this\ filename```
### Level 3->4:
Use 
```cat .hidden```
### Level 4->5:
Use 
```cat ./-file07```
### Level 5->6:
Use 
```find -type f -size 1033c ! -executable ```
### Level 6->7:
Use 
```find / -size 33c -group bandit6 -user bandit7```
### Level 7->8:
Use 
```grep millionth data.txt```
### Level 8->9:
```sort data.txt|uniq -u```
### Level 9->10:
Use 
```strings -es data.txt```
### Level 10->11:
```base64 -d data.txt```
### Level 11->12:
Use 
```ls```
and then 
```cat data.txt```
again 
```cat data.txt | tr a-zA-Z n-za-mN-ZA-M```
### Level 12->13:
Decompress the file back to its prev form
### Level 13->14:
Use  
```sshkey.private to ssh into bandit14@localhost and cat /etc/bandit_pass/bandit14	```
### Level 14->15:
Use 
```nc localhost 30000```
### Level 15->16:
Simply 
```cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -ign_eof (to ignore end of line)```
### Level 16->17:
Use nmap to scan and we see the open port 31790
```cat /etc/bandit_pass/bandit16 | openssl s_client -connect localhost:31790 -ign_eof```
