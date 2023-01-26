# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

# PrometeoCTF 23

## (I do not remember the names of some of the challenges ,hence I've added my own names 😅)

### Challenge #1 - Based

The First Challenge was pretty easy 
converting the given text into base 64 gave me the flag

prometeoCTF{TToRS3TROD31SFUN}

### Challenge #2 - Tuk Tuk ... Tuuuuk


I had to download a .wav files 
it had a lot of beeps and pauses hence used a morse code decoder to get the message

prometeoCTF{m0rs3_cod3_1s_fun}

### Challenge #3 - Basic but cool 

This challenge was pretty interesting 

This was the P.S

          Are you smart enough to decipher this? Think thrice before you do it

          L2IvraWapzWDE1A7Z19GAUOaZTIsATuaqI95raZ0ZU0=

Gave me the idea of it being base64
tried to convert it into base64 but it resulted in a junk val 
Tried to use caesar cipher with base64

[M2JwsbXbqaXEF1B7A19HBVPbAUJtBUvbrJ95sbA0AV0=,
N2KxtcYcrbYFG1C7B19ICWQcBVKuCVwcsK95tcB0BW0=,
O2LyudZdscZGH1D7C19JDXRdCWLvDWxdtL95udC0CX0=,
P2MzveAetdAHI1E7D19KEYSeDXMwEXyeuM95veD0DY0=,
Q2NawfBfueBIJ1F7E19LFZTfEYNxFYzfvN95wfE0EZ0=,
R2ObxgCgvfCJK1G7F19MGAUgFZOyGZagwO95xgF0FA0=,
S2PcyhDhwgDKL1H7G19NHBVhGAPzHAbhxP95yhG0GB0=,
T2QdziEixhELM1I7H19OICWiHBQaIBciyQ95ziH0HC0=,
U2ReajFjyiFMN1J7I19PJDXjICRbJCdjzR95ajI0ID0=,
V2SfbkGkzjGNO1K7J19QKEYkJDScKDekaS95bkJ0JE0=,
W2TgclHlakHOP1L7K19RLFZlKETdLEflbT95clK0KF0=,
X2UhdmImblIPQ1M7L19SMGAmLFUeMFgmcU95dmL0LG0=,
Y2VienJncmJQR1N7M19TNHBnMGVfNGhndV95enM0MH0=,
Z2WjfoKodnKRS1O7N19UOICoNHWgOHioeW95foN0NI0=,
A2XkgpLpeoLST1P7O19VPJDpOIXhPIjpfX95gpO0OJ0=,
B2YlhqMqfpMTU1Q7P19WQKEqPJYiQJkqgY95hqP0PK0=,
C2ZmirNrgqNUV1R7Q19XRLFrQKZjRKlrhZ95irQ0QL0=,
D2AnjsOshrOVW1S7R19YSMGsRLAkSLmsiA95jsR0RM0=,
E2BoktPtisPWX1T7S19ZTNHtSMBlTMntjB95ktS0SN0=,
F2CpluQujtQXY1U7T19AUOIuTNCmUNoukC95luT0TO0=,
G2DqmvRvkuRYZ1V7U19BVPJvUODnVOpvlD95mvU0UP0=,
H2ErnwSwlvSZA1W7V19CWQKwVPEoWPqwmE95nwV0VQ0=,
I2FsoxTxmwTAB1X7W19DXRLxWQFpXQrxnF95oxW0WR0=,
J2GtpyUynxUBC1Y7X19EYSMyXRGqYRsyoG95pyX0XS0=,
K2HuqzVzoyVCD1Z7Y19FZTNzYSHrZStzpH95qzY0YT0=]
 
tried converting it with a simple .py script but no luck

Finally used cyberchef to decrypt using the following receipe

   (N-ZA-Mn-za-m0-9+/=)

PrometeoCTF{3_F4ct0r_4uth_lmf40}



Overall this CTF was fun... We got to 17th position 


