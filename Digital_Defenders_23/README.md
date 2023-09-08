# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

# Digital Defenders CTF 2023 

This was 3 day national level CTF organized by [bi0s](https://bi0s.in/), Cisco and CysecK which was really intriguing . I ended up getting 12th position overall which is **3rd Place** 

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
## Wojtek’s Enigma

The flag is encrypted using “Enigma Machine” . Directly plug in the given parmeters in an online enigma machine decoder and enter the ciphertext , and you will get the flag .

`flag{wojtek_7h3_be4r}`

## MOD

In the challenge, all the characters are modded with 97. Important thing to note here is that the maximum possible value for a character is 125 (for ‘}’) There are two possible cases when it’s modded:

The character is above 97, but below 125. This implies that it will be lesser than 28 when modded with 97.
The character is below 97, which means that the mod operation does nothing. The character’s preserved!
Using this information, we can check if each number is below the threshold or not. If it is, we can just add 97 to it to get the original character. If it isn’t, we can just mod it with 97 to get the original character.

```
from string import ascii_letters, digits
L = [5, 11, 0, 6, 26, 77, 48, 3, 20, 49, 48, 95, 12, 52, 10, 51, 18, 95, 55, 7, 8, 13, 6, 18, 95, 11, 48, 48, 15,28]
f = ''
for i in L:
    if i>28:
        f += chr(i)
    else:
        f += chr(i+97)
```
## 7h3_Analyst

This was a really cool challenge which can be solved using `voltality` 
that the key is stored in the envars there is a file where the password has to be bruteforced and the internet history has to checked

we find the clue that the key is biosdfir 
On performing filescan to get the password encrypted file
`vol.py -f chall.raw --profile=Win7SP1x86 filescan`
we extract the zip file using dumpfiles plugin

On bruteforcing the zip using john the ripper. The password is batman33. The txt inside the zipfile is
`bhfshqsejovlgkqi`

now before decoding the text, checking the chromehistory using the plugin chromehistory.

`vol.py --plugins=plugin/ -f chall.raw --profile=Win7SP1x86 chromehistory`

The only site visted is pastebin and it asked for a password which will probably be the encrypted code which we got from the zip file.

On using decode to figure out the encryption(i.e Vigenere Cypher).Decription is done by giving the key biosdfir.Which decrypts the text and gives us the password to the pastebin :

`azraelknightdfir`

the pastebin contains the flag
