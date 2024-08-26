# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

# Cache Timing Analysis on Cryptographic operations

When it comes to hardware security, side channel analysis is one of the most widely used attacks.
To understand this lets try to understand what cache timing attacks are

In this timing attack, the attacker attempts to compromise a cryptosystem by analysing the time 
taken to execute cryptographic algorithms

Every logical operation in a computer takes time to execute, and the time can differ based on the input
and with precise measurements of the time for each operation, an attacker can work backwards to the input.
Finding secrets through timing information may be significantly easier than using cryptanalysis of known 
plaintext, ciphertext pairs.

When sensitive data is accessed, it may be cached, leading to faster subsequent accesses. 
By measuring these timing differences, you can infer which data was accessed and possibly 
reconstruct secret keys or sensitive information.


To understand this a bit more deeper..

Lets take a linux library file say libcrypto 

The OpenSSL crypto library (libcrypto) implements a wide range of cryptographic algorithms used in various 
Internet standards. The services provided by this library are used by the OpenSSL implementations of TLS 
and CMS, and they have also been used to implement many other third party products and protocols.

looking at the library functions using 'nm' command 

nm -D /usr/lib/libcrypto.so | less

-D is for dynamic

we can see that the function uses  



00000000000bf380 T AES_bi_ige_encrypt@@OPENSSL_3.0.0
00000000000bd0a0 T AES_cbc_encrypt@@OPENSSL_3.0.0
00000000000bef40 T AES_cfb128_encrypt@@OPENSSL_3.0.0
00000000000bef60 T AES_cfb1_encrypt@@OPENSSL_3.0.0
00000000000bef80 T AES_cfb8_encrypt@@OPENSSL_3.0.0
00000000000bcaf0 T AES_decrypt@@OPENSSL_3.0.0
00000000000befa0 T AES_ecb_encrypt@@OPENSSL_3.0.0
00000000000bc560 T AES_encrypt@@OPENSSL_3.0.0
00000000000befc0 T AES_ige_encrypt@@OPENSSL_3.0.0
00000000000bf6d0 T AES_ofb128_encrypt@@OPENSSL_3.0.0
00000000000bf6c0 T AES_options@@OPENSSL_3.0.0
00000000000bce70 T AES_set_decrypt_key@@OPENSSL_3.0.0
00000000000bcbb0 T AES_set_encrypt_key@@OPENSSL_3.0.0
00000000000bf710 T AES_unwrap_key@@OPENSSL_3.0.0
00000000000bf6f0 T AES_wrap_key@@OPENSSL_3.0.0



these functions for the AES Encryption / Decryption

then i wrote a small C program that uses these functions to try and figure out how these functions are being used in real time.


