# dont-use-client-side

## Overview

Points: 100
Category: Web Exploitation

## Description
Can you break into this super secure portal? https://jupiter.challenges.picoctf.org/problem/17682/ or http://jupiter.challenges.picoctf.org:17682 

Link will differ from user to user

## Hints
1. Never trust the client

## Approach

First hint that I got was from the challenge description, which said "dont user client side".

So this has something to do with client side.

Upon opening the link, the web page showed a basic login screen with just the password as input.

![dont use client side homepage](/picoCTF/img/dont%20use%20client%20side%201.png)

I tried using common passwords like 123456 and pasword but none of them worked.

<!-- add error logging in image -->
![dont use client side incorrent password](/picoCTF/img/dont%20use%20client%20side%202.png)

Then I went to view the source code for this web page, which is shown below:

<!-- Add view source page screenshot here -->
![dont use client side source code](/picoCTF/img/dont%20use%20client%20side%203.png)

It was pretty clear that the flag was in the source code. 

Now the main challenge was to get the flag from the source code. We can approach it using 2 ways:
1. Copy pasting the raw flag from source code itself.
2. Writing a script to get the flag by parsing through the source

Since this challenge looked pretty easy for me, I would have preferred to go with the 1<sup>st</sup> option as that would have been faster and easier than writing a script to parse through the source code.

But I to wrote the code to get the flag from the source code itself in this challenge.

```python
#!/usr/bin/env python

#Get the requests package to send requests
# 'pip install requests' if your system does not have the package installes
import requests

r = requests.get('put-your-link-for-the-challenge')

# We now parse the source code and get all the lines
lines = r.text.split('\n')

# Since we know that the flag content is in the line that has if conditions, we extract only those lines
lines = [l for l in lines if 'if ' in l]

# Cleaning up the extracted lines
lines = [l.split('==') for l in lines]

# Here:
#   1. The lambda function is used to clean the first eleme nt of the lines list and remove the single quotes(') from the second element. It returns a clean-up tuple of text 
#   2. The map function applies the lambda function to all the lines list element 
#   3. The sorted function then sorts out all the elements of the lines list in ascending order.
#   4. Finally the list function makes the whole output in a form of list
lines = list(
            sorted(
                map(
                    lambda x: (x[0].strip(), x[1].split('\'')[1]),
                    lines
                    )
                )
            )


# We now form the whole flag
s = ''
s += lines[0][1]
s += lines[-1][1]
for l in lines[1:-1]:
        s += l[1]

# Then we print the flag
print(s)

```

## Flag
We finally the get as : picoCTF{no_clients_plz_b706c5}