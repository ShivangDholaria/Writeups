# GDB baby step 1

## Overview

Points: 100

Category: Reverse Engineering

## Description
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where n is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Download the assembly dump `here`.

## Hints (if any)
1. gdb is a very good debugger to use for this problem and many others!
2. `main` is actually a recognized symbol that can be used with gdb commands.

## Approach

Okay so we are given the actual executable rather than the text file containing instructions. We can see what kind of file it is by using `file` command.

![File command](./img/gdb%20baby%20step%201%201.png)

Let's first run it to see if it produces any output.

![output of the challenge file](./img/gdb%20baby%20step%201%203.png)

We get not output so lets open the file in some reverse engineering tool.

I used ghidra to disassemble the executable and look at what is in the `eax` register. But lets try it with gdb!

Install `gdb` if you don't have it in your system and open file in `gdb`.

```bash
gdb file-name
```
![file opened in gdb](./img/gdb%20baby%20step%201%202.png)

Then we type `info funcions` to list out all the funtions present in the executable.

![function list](./img/gdb%20baby%20step%201%204.png)

We see `main` being listed in the list so lets disassemble it and see what the code is.

![Disassembled main](./img/gdb%20baby%20step%201%205.png)

Here, we can clearly see the instruction `mov $0x86342, %eax` is putting hard coded value in register `eax`. So converting that value `0x86342` to decimal is `549698`.

This is the required flag.

## Flag
picoCTF{549698}