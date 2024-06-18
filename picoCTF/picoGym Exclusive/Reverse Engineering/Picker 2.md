# Picker 2

## Overview

Points: 100

Category: Reverse Engineering

## Description
Can you figure out how this program works to get the flag? Connect to the program with netcat: 

`$ nc saturn.picoctf.net 64676`

The program's source code can be downloaded `here`.

## Hints (if any)
1. Can you do what `win` does with your input to the program?

## Approach
Ahh, a nice challenge. Same as previous one([You can find it here](./Picker%201.md)) the approach will be the same, but there is a twist. Here the code filer's out the `win` input when entered. So what to do now?

![win filter code](./img/Picker%202%201.png)

Even after trying with different input variation, the result is same. So let's try something that called a command injection. Since in the source code, we see that `sys` is being imported, maybe we can pass in os functions and see we are able to get any output.

![os import](./img/Picker%202%202.png)

Lets try to give `print(sys.version)` to get the current of python interpreter present in the system.

![interpreter version](./img/Picker%202%203.png)

We see that command injection works so lets get the flag!

```python3
print(open('flag.txt', 'r').read())
```

![flag](./img/Picker%202%204.png)



## Flag
picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_b924e8e5}
