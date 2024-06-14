# Bit-O-Asm-2

## Overview

Points: 100

Category: Reverse Engineering

## Description
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where n is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Download the assembly dump `here`.

## Hints (if any)
1. `PTR`'s or 'pointers', reference a location in memory where values can be stored.
## Approach
This too is similar to [Bit-O-Asm-1](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/Bit-O-Asm-1.md) challenge where we need to find the value present in the `eax` register.

We find print out the contents of the downloaded file and examine it.

![File content](./img/bit%200%20asm%202%201.png)

We see a command `mov eax, DWORD PTR [rbp-0x4]`. And above that line we see the command `mov DOWRD PTR [rbp-0x4], 0x9fe1a`. Well, it seems like this is our flag.

`0x9fe1a` in decimal is `654874` as we need our flag to be in decimal.

## Flag
picoCTF{654874}