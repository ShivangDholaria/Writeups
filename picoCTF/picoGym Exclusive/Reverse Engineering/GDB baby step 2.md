# GDB baby step 2

## Overview

Points: 100

Category: Reverse Engineering

## Description

Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where n is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. 

Debug this.

## Hints (if any)
1. You could calculate `eax` yourself, or you could set a breakpoint for after the calculcation and inspect eax to let the program do the heavy-lifting for you.
## Approach

Same as previous challenge, lets debug the executable.

But first, the basic checks. Lets find what kind of file it is and if it produces any output.

![file type](./img/gdb%20baby%20step%202%201.png)

![file output](./img/gdb%20baby%20step%202%202.png)

Now opening it up in `gdb`, lets see if the main function is present and disassemble it.

![list of functions](./img/gdb%20baby%20step%202%203.png)

![disassembled main](./img/gdb%20baby%20step%202%204.png)

We can see lot happening in the program. So to save out time, lets set a breakpoint just before the program completes its execution and find out what value is present in the register `eax`.

To set a breakpoint, we write the following command:
```bash
break *address
```
Here, the memory address is written in blue like `0x0000000000401106`. Since, we dont need all the leading zeroes, we can discard them.

So we set the break point at address `0x401141`, and run the code. We will hit the breakpoint when it reaches the line where we have placed our breakpoint.

Once we hit the breakpoint, we will get the following message:

![breakpoint hit](./img/gdb%20baby%20step%202%205.png)

Then we can easily find the value present in `eax`. To see the value, we just type `info register eax` or `i r eax` for short notation.

![eax value](./img/gdb%20baby%20step%202%206.png)

And there's our flag!

## Flag
picoCTF{307019}