# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

# CSA-CTF
## BITS-PILANI HYDERABAD

### Chamber of Secrets
The numbers are in binary form. They need to be converted into decimal numbers first.
These decimal numbers can be converted to alphabetical form in the manner: 1 for a, 2
for b, 3 for c and so on. The three lines on conversion will give the following output:
dhbwkoej
```csactfadgbvcxpit```
ndknfjfb
Since the second line is of the form csactf*, ```adgbvcxpit``` is the final answer.
### Broken is its own secure
Sending this executable over to my friend. Yeah it has secrets but its segfaulting and
broken so no one can see it anyways.
Binary file: gg
This is an executable file and simply opening it in a text editor will give garbage.
What you need to do is see the strings of the file. Either strings gg or cat gg works.
The flag is split here so using grep wont work. You’ll have to actually search through the
output but it’s easy enough.
Flag: ```csactf{bin-aryf-ile}```
### Watch the world burn:
On going to inspect element, we find a comment with the following sequence:
csa_ctf{*____ ***__ **___ ****_}. It is morse which translates to 1,3,2,4. On rearranging
the sets of letters in the left menu in the above order, we get the following sequence:
```jtfkqnwbspam```. It is the password to the next file.
### BLOGIFT
This is the start of my career as a blog star! Eeeeek!
Blogift
Just expand all the divs in the Elements section of inspect element.
Flag: ```csactf{zyp-phns-ool}```
### Close to your friends
I’ve been told everything in life will work out if you have good friends. So I made my own
cipher
where all the letters are with their best friends :3
Ciphertext: vdsvyg}nrg=torm=fdd\
Solution:
Replace each character with the one to its left on the qwerty keyboard.
Flag:```csactf{bef-rien-dss}```
### Where is the hidden door?
Use openStego with the password philosopher (which is blacked out in the image).
### Fun with XOR’s
XOR operation has the property that if x⊕y = z, then y = x⊕z. Since you already know
that the flag is of the form csa.... , you can figure out the key, by taking XOR of the first
character of the encrypted message and the character c. Once you have the key, take
XOR of the encrypted message with the key to get the decrypted message
```csactf{math_is_love}```
### Open the Pandora Box
As many of you may have already figured from the question title, the task is to obtain
the key from the program given, and use it to get the flag hidden inside the image file.
There are several ways to obtain the key. One way is to brute force through all
possibilities (the question states that the key is a 6 digit number). Now check for which
value the given input maps to the given output. Note that exponentiation is a step which
could create a problem here if you don’t use a fast algorithm. (For the unversed, I
suggest reading up binary exponentiation). Once you have the key, use OpenStego
software to decrypt the image.
### Hidden Message(s) solution:
We will need openStego and winrar for extracting the flags, as pointed out in the
question. The only observation was that the passwords are the longer strings without
brackets. The first part of the flag is ‘csac’
1. Open the img.png in openStego, choose a folder, and click on ‘Extract Data’, there
is no password here.
2. You will see a file named message.zip, extract the contents using winrar, the
password will be the string in the first image i.e. vcpwiyt.
3. The extracted files contain an image with the second part of the flag ‘tf{oot’ and the
second password prbmccv.
4. You can extract the final text file from the final.zip using the second password,
which will have the third part of the flag i.e ‘emesirprus}’ and a congratulatory
message.

### WE LURK IN THE DARK
Muzan-sama made a portal for us Moons. Hashiras gonna be sweating when they see
this website we’re gonna be using against them.
Moon App
You need to two things to solve this: the vigenere key hidden in the page (elements) and
also the ciphertext of username and password. You can see these either in localstorage
or the sources section. Do a vigenere decrypt (facilities for these exist online) , enter it
in the form and voila.
```Flag: csactf{muz-ansa-maa}```

### Modified Rolling hash function solution:
It was given as a note that the values of the parameter c are less than 97( ASCII of ‘a’),
and also that the parameter p is a positive integer.
Now, Given that the hash function is of the format.
The s[k] – c terms differ in their original manner, i.e. on decreasing every character by c,
the original differences are preserved. So, then we can just take the offsets from ‘a’ and
adjust for c later on. For example {‘v’ – c, ’i’ – c, ‘b’ – c} can be written as {x + ‘v’ – ‘a’, x
+ ‘i’ – ‘a’, x + ‘b’ – ‘a’}, or {x + 21, x + 8, x +1}.
Now, we can iterate over the values of p, starting from 1 and incrementing till we find a
valid answer. So for every p, we will first calculate the value of x from the first equation
after doing the substitution described above. Firstly, it should be a non-negative integer,
and secondly, it should satisfy all the other given equations as well.
Once we have found such a p(43 in this case) and x that satisfies all the relations, we
can easily get the value of c from any substitution using x.
Now that you’ve figured out the p and c, all that remains is to find out the original three
encrypted keys, they can be easily found by brute-forcing through the possible
candidates, hashing them using the parameters and the given hash function, and
comparing the hashes, which is feasible since the number of characters to permute is
six.

### ONE BIRD FOR ANOTHER
I’ve made my own birdy hash cuz I like birds. Someone told me they can find collisions
but they’re probably just jealous that they can’t fly.

subHash.py
Look for repetitions in the BIRD_BOX, that is two keys with same value, but make sure
the value is of same datatype as that of the key, because otherwise you’ll enter the
randomising if-block (though you could potentially bruteforce that as well)
Two inputs which collide are: abcdkovh69 and abcdkovh61
Flag: ```csactf{urh-ashr-ekt}```
### RANDOMBIGGOOD
RSA is so fun and easy!
bigRSA.py
Notice how the modulus is constructed - by multiplying small primes. This means it can
be factorised quickly.
Multiplying by (N+1) does nothing due to modular arithmetic (N+1 % N = 1)
After getting the factors, you have to calculate Euler’s totient. For multiple primes pi, it’s
the product of pi - 1 for all i.
Just calculate the private key [inverse(e,phi)] and get the plaintext.
Flag: ```csactf{https://forms.gle/Vz8CPDV8CZkfdH5F8}```