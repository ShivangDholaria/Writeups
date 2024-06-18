# Picker 3

## Overview

Points: 100

Category: Reverse Engineering

## Description
Can you figure out how this program works to get the flag? Connect to the program with netcat: 

`$ nc saturn.picoctf.net 54565`

The program's source code can be downloaded `here`. The binary can be downloaded `here`.

## Hints (if any)
1. With Python, there are no binaries. With compiled languages like C, there is source code, and there are binaries. Binaries are created from source code, they are a conversion from the human-readable source code, to the highly efficient machine language, in this case: x86_64.

2. How can you find the address that win is at?

## Approach
Okay, this time we got a C source file as well as an executable binary.

Looking at the source file, we see that there's the win function. And the main function takes in the address of where the win function is located in the memory space.

![source code](./img/Picker%204%202.png)

If we open up the executable in ghidra and search for `win` function, we find the address of its entry point

![ghidra output](./img/Picker%204%201.png)

Here we can see that `0040129e` is where the entry for the `win` function is. Now, we put that address in the server, we get the flag!

![flag](./img/Picker%204%203.png)

## Flag
picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_01672a61}