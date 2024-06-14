# Bit-O-Asm-1

## Overview

Points: 100

Category: Reverse Engineering

## Description
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where n is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Download the assembly dump `here`.

## Hints (if any)
1. As with most assembly, there is a lot of noise in the instruction dump. Find the one line that pertains to this question and don't second guess yourself!

## Approach
This challenge is simple as well. We just need to know what value is in the regist `eax`. 

We first download the given file and see the contents of the file.

![File content](img/bit%200%20asm%201%201.png)

We can clearly see that register `eax` has value of `0x30`. And `0x30` in decimal is `48`. You might have a different value so you will need to change the given answer.

Pretty easy ain't it!

## Flag
picoCTF{48}