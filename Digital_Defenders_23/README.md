# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

# Digital Defenders CTF 2023 

This was 3 day national level CTF organized by [bi0s](https://bi0s.in/), Cisco and CysecK which was really intriguing . I ended up getting **12th** place.
So writeup covers some of the interesting challenges from the CTF.

Digital Forenscis was the most intresting cateogry in my opinion.

## Alw4y5_h4s_b33n [Digital-Forensics]
  
  *Had to resize the jpg file to correct dimensions according to exif data*

## C4pt4inC0ld [Digital-Forensics]
  
  *I had to do White space analysis, so using `snow` gives us the flag*

## brut3nf0rce [Digital-Forensics]

  - Had to bruteforce the zip file with a custom wordlist generated using `crunch` since the chall-desc mentioned the password is less than 3 characters
	and then got an image
  - Bruteforce the image again with `rockyou.txt`
	which got me the flag

## Flawless AES

Observing the code we understand that we use iv1 as key for encrypting secret
So we decrypt ciphertext1 that is of length 64 bytes, same as length of secret
Since CBC mode is used, the plaintext was initially xored with key , since the key for the flag is passed as iv for secret
So after decrypting ciphertext1 xor with secret (given in the script), and retrieve the first 16 bytes that is your key.
Now you have key and iv2 used to encrypt flag
Decrypt the flag using pycrypto library

This is the solution :
```
from Crypto.Cipher import AES
from pwn import xor

with open("encrypted", "rb") as f:
    iv1 = f.read(16)
    ciphertext1 = f.read(64)
    iv2 = f.read(16)
    ciphertext2 = f.read()

secret = b"This is top secret message. I hope, no one can intercept UwU !!!"

cipher = AES.new(iv1, AES.MODE_ECB)
decrypted = cipher.decrypt(ciphertext1)

key = xor(decrypted,secret)[:16]

cipher = AES.new(key,AES.MODE_CBC,iv2)
plaintext = cipher.decrypt(ciphertext2)

plaintext = plaintext.rstrip(b"\0")

print(f"Plaintext: {plaintext.decode()}")
```
