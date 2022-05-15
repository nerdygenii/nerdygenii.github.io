---
layout: post
title: CYSEC CTF 2022 walkthrough
categories: [CTF]
tags: [Capture the flag, CYSEC, breadcrumbs]
---


## PREFACE
  This is a write up on the national cysec ctf So i decided i'll be writing on challenges that i solved first during the competition, when i'm a little less busy i'll make a writeup on other challenges.
  
## Web 
#### Breadcrumbs
What do they say about cookies?
No need for brute forcing please
http://34.205.69.93:3000/
![image](/assets/assets/img/posts/CYSEC/breadcrumbs/0.5.png)

nice, let's open the link http://34.205.69.93:3000/

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/1.png)

hmm we got this! let's check things we can find, so i decided to scan around manally and see functions that are available clicked on the Auth dropdown

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/1.5.png)

i decided to register to see what happens

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/2.png)

hmm nothing much just this

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/3.png)

let's try to login let's see what happens

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/4.png)

logged in got into the dashboard, since the dashboard was talking about cookies, decided to check out my cookies i found out it's base64..then tried to decrypt, got my username and password

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/5.png)
tried submitting my cookies, sighs* here's what i got

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/5.5.png)
as i was taking notes of possible endpoints, decided to check out other functionalities
oh! yeah it was the support's time let's check out support

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/6.png)
hmm it says "where will you like to steal cookies from" and it also says "tell us where we can reach you".. so i thought why dont you check out the request sent to me..so i lit up my ngrok
```Ngrok is a cross-platform application that helps you serve your local ports to the internet. to get one you can just download it from```[here](https://ngrok.com/download)
so i used this command to lit it up
```
┌─[nerdy@genii]─[~]
└──╼ $ngrok http 8000

ngrok: name of the tool
'http' argument tells the tool to start an http tunnel so you can receive the http request sent
8000 tells it to send the request to port 8000
```
then i set up my netcat to listen on port 8000 with this command
```
┌─[nerdy@parrot]─[~]
└──╼ $nc -lnvp 8000

nc: name of the tool
-lnvp is the same as -l -n -v -p
-l tells it to listen
-n tells it numeric-only IP addresses, no DNS
-p tells it what port to listen on
```

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/8.png)
i filled the form up the form with my details

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/9.0.png)
submitted and waited for the request from support and boom!! the request came with a cookie

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/9.png)
so let's submit it, i logged in and put the cookie

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/10.png)
submitted...........and...yayyy!! it was correct and we got our flag

![image](/assets/assets/img/posts/CYSEC/breadcrumbs/11.png)


yeah that's all about Breadcrumbs, nice right? will drop the remaining when i'm less busy.. 

thanks for reading, ありがとうございました (Arigatōgozaimashita)
