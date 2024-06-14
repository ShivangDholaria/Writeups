# Bit-O-Asm-3

## Overview

Points: 100

Category: Reverse Engineering

## Description

Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where n is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Download the assembly dump `here`.

## Hints (if any)
1. Not everything in this disassembly listing is optimal.

## Approach
This is somewhat more complex than the its predecesors, but is do able. For this challenge, you need to know basic commands of assembly language such as `mov`, `imul`, `add`, etc. 

We download the given file and print out it's contents.

![file contents](./img/bit%200%20asm%203%201.png)

Looks like we need to some calculation so open up the file in a text editor.

![text editor](./img/bit%200%20asm%203%202.png)

Firstly, we see that some values such as `0x9fe1a` and `0x4` are being stored in some memory location. 
Then `0x9fe1a` is being moved to `eax`.

Now, `eax` is being multiplied by `0x4` and then `0x1f5` is being added. 

Finally, the value to `eax` is being stored in some other memory location and then again in `eax` register.

![All calulations](./img/bit%200%20asm%203%203.png)

After all the computation, we get the final value as `0x27fa5d` which is 261999 in decimal.

That's it for this challenge.

## Flag
picoCTF{2619997}