# GDB baby step 4

## Overview

Points: 100

Category: Reverse Engineering

## Description

`main` calls a function that multiplies `eax` by a constant. The flag for this challenge is that constant in decimal base. If the constant you find is 0x1000, the flag will be `picoCTF{4096}`.

Debug `this`.

## Hints (if any)
1. A function can be referenced by either its name or its starting address in gdb. 

## Approach

This is a simple challenge as we just need to find the constant that will give us our flag. 

So lets start with all the file type finding and executing it.

![File type](./img/gdb%20baby%20step%204%201.png)

![Executing file](./img/gdb%20baby%20step%204%202.png)

Now lets launch the file in gdb and debug it. First change the disassembly flavor to intel.

![setting disassembly flavor](./img/gdb%20baby%20step%204%203.png)

Now lets list all the functions present.

![listing all functions](./img/gdb%20baby%20step%204%204.png)

We see something new this time. We see a function `func1` present in the list. So lets disassemble itand see what's there.

![Disasssemblt func1](./img/gdb%20baby%20step%204%205.png)

And there's the constant that's being multiplied by `eax`. `0x3269` in hex is `12905` in decimaal. 
## Flag
picoCTF{12905}