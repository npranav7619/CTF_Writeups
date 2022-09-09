# Welcome to Neouchiha's Blog

### Feel Free to Look at my CTF_Writeups and other Projects.

[Home](https://npranav7619.github.io/)
[CTF_Writeups](https://npranav7619.github.io/CTF_Writeups)
[About Me](https://npranav7619.github.io/Aboutme)

# TryHackMe
# Burp Suite
## Overview of Features

### 1 Which tool in Burp Suite can we use to perform a ‘diff’ on responses and other pieces of data?

Comparer

### 2 What tool could we use to analyze randomness in different pieces of data such as password reset tokens?

Sequencer

### 3 Which tool can we use to set the scope of our project?

Target

### 4 While only available in the premium versions of Burp Suite, which tool can we use to automatically identify different vulnerabilities in the application we are examining?

Scanner

### 5 Encoding or decoding data can be particularly useful when examining URL parameters or protections on a form, which tool allows us to do just that?

Decoder

### 6 Which tool allows us to redirect our web traffic into Burp for further examination?

Proxy

### 7 Simple in concept but powerful in execution, which tool allows us to reissue requests?

Repeater

### 8 With four modes, which tool in Burp can we use for a variety of purposes such as field fuzzing?

Intruder

### 9 Last but certainly not least, which tool allows us to modify Burp Suite via the addition of extensions?

Extender

## Proxy 
#2 By default, the Burp Suite proxy listens on only one interface. What is it? Use the format of IP:PORT

127.0.0.1:8080

### 4 Return to your web browser and navigate to the web application hosted on the VM we deployed just a bit ago. Note that the page appears to be continuously loading. Change back to Burp Suite, we now have a request that’s waiting in our intercept tab. Take a look at the actions, which shortcut allows us to forward the request to Repeater?

CTRL-R

### 5 How about if we wanted to forward our request to Intruder?

CTRL-I

### 6 Burp Suite saves the history of requests sent through the proxy along with their varying details. This can be especially useful when we need to have proof of our actions throughout a penetration test or we want to modify and resend a request we sent a while back. What is the name of the first section wherein general web requests (GET/POST) are saved?

HTTP history

### 7 Defined in RFC 6455 as a low-latency communication protocol that doesn’t require HTTP encapsulation, what is the name of the second section of our saved history in Burp Suite? These are commonly used in collaborate application which require real-time updates (Google Docs is an excellent example here).

WebSockets history

### 8 Before we move onto exploring our target definition, let’s take a look at some of the advanced customization we can utilize in the Burp proxy. Move over to the Options section of the Proxy tab and scroll down to Intercept Client Requests. Here we can apply further fine-grained rules to define which requests we would like to intercept. Perhaps the most useful out of the default rules is our only AND rule. What is it’s match type?

URL

### 9 How about it’s ‘Relationship’? In this situation, enabling this match rule can be incredibly useful following target definition as we can effectively leave intercept on permanently (unless we need to navigate without intercept) as it won’t disturb sites which are outside of our scope — something which is particularly nice if we need to Google something in the same browser.

Is in target scope

## Target Definition

### 5 Browse around the rest of the application to build out our page structure in the target tab. Once you’ve visited most of the pages of the site return to Burp Suite and expand the various levels of the application directory. What do we call this representation of the collective web application?

site map

### 6 What is the term for browsing the application as a normal user prior to examining it further?

happy path

### 8 The issue definitions found here are how Burp Suite defines issues within reporting. While getting started, these issue definitions can be particularly helpful for understanding and categorizing various findings we might have. Which poisoning issue arises when an application behind a cache process input that is not included in the cache key?

Web cache poisoning

## Puttin’ it on Repeat[er]

### 2 Try logging in with invalid credentials. What error is generated when login fails?

Invalid email or password.

### 4 Now that we’ve sent the request to Repeater, let’s try adjusting the request such that we are sending a single quote (‘) as both the email and password. What error is generated from this request?

SQLITE_ERROR

### 8 What field do we have to modify in order to submit a zero-star review?

rating

## Help! There’s an Intruder!
### 1 Which attack type allows us to select multiple payload sets (one per position) and iterate through them simultaneously?

Pitchfork

### 2 How about the attack type which allows us to use one payload set in every single position we’ve selected simultaneously?

Battering Ram

### 3 Which attack type allows us to select multiple payload sets (one per position) and iterate through all possible combinations?

Cluster Bomb

### 4 Perhaps the most commonly used, which attack type allows us to cycle through our payload set, putting the next available payload in each position in turn?

Sniper

### 12 Finally, click ‘Start attack’. What is the first payload that returns a 200 status code, showing that we have successfully bypassed authentication?

a' OR 1=1 —
