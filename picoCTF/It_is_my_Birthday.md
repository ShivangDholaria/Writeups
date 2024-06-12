# It is my Birthday

## Overview

Points: 100

Category: Web Exploitation

## Description
I sent out 2 invitations to all of my friends for my birthday! I'll know if they get stolen because the two invites look similar, and they even have the same md5 hash, but they are slightly different! You wouldn't believe how long it took me to find a collision. Anyway, see if you're invited by submitting 2 PDFs to my website. 

http://mercury.picoctf.net:48746/

## Hints (if any)
1. Look at the category of this problem.
2. How may a PHP site check the rules in the description?

## Approach

This looked kinda interesting as it talks about a very old attack called Birthday attack. To explain this attack in short, it is basically finding out which 2 files that are entirely different, but have same hash value. 

Since the challenge tells the user to upload 2 pdf files, we need to find out if there exists 2 such files. 

<!-- image of site -->
![It is my birthday homepage](img/its%20my%20birthday%201.png)

Firstly, I tried uploading some files with different types like .zip, .docx, etc.

![Error message for different file types](img/its%20my%20birthday%202.png)

I got an error "not a PDF"

![Error message for different file types](img/its%20my%20birthday%209.png)

Then, I got some sample pdfs that I tried to upload.

![Upload different pdf files](img/its%20my%20birthday%207.png)

I got the error message stating MD5 hash is not same

![MD5 not same error message](img/its%20my%20birthday%204.png)

So I tried to upload the same pdfs with different names thinking it might work but it didn't.

![Upload same pdf file with different name](img/its%20my%20birthday%208.png)

![Upload same pdf file with different name](img/its%20my%20birthday%203.png)


Then after browsing through the web, I came across a very useful resource that explains how the birthday attack works.

https://www.mscs.dal.ca/~selinger/md5collision/

This resouce has executable files for windows as well as linux that are different but have the same hash. So I downloaded the linux version and saved the files with .pdf as extension.

Then I tried uploading it and viola! 

It worked!

![Upload same pdf file with different name](img/its%20my%20birthday%206.png)

![Upload same pdf file with different name](img/its%20my%20birthday%205.png)

You can see the flag commented out.

## Flag
picoCTF{c0ngr4ts_u_r_1nv1t3d_aebcbf39}