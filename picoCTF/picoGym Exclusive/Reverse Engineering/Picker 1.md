# Picker 1

## Overview

Points: 100

Category: Reverse Engineering

## Description
This service can provide you with a random number, but can it do anything else? Connect to the program with netcat:

 `$ nc saturn.picoctf.net 55669` 

The program's source code can be downloaded `here`.

## Hints (if any)
1. Can you point the program to a function that does something useful for you?

## Approach
This was a pretty interesting challenge. To find the flag, we needed to enter the function name which would get us the flag. After the downloading and running the file, it was clear that all we needed was to write the function name.

![Source code](./img/Picker%201%201.png)

![Source code](./img/Picker%201%202.png)

![Source code](./img/Picker%201%203.png)

On a closer inspection of the source code, we see the function `win` which was the needed function to get the flag.

On connecting to the server and entering `win`, we get the flag encoded in hex. So we just need to unhex it and we are good to go!

![Hex flag](./img/Picker%201%204.png)

```python3
s = ''
with open('hexflag.txt') as flagfile:
    for l in flagfile:
        s += chr(int(l, 16))

print(s)
```

I wrote the code above to unhex the encoded flag. You can also use online tools if you prefer them, you choice!


## Flag
picoCTF{4_d14m0nd_1n_7h3_r0ugh_b523b2a1}