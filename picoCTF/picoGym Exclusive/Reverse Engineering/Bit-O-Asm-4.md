# Bit-O-Asm-4

## Overview

Points: ---

Category: ---

## Description
Can you figure out what is in the `eax` register? Put your answer in the picoCTF flag format: `picoCTF{n}` where n is the contents of the `eax` register in the decimal number base. If the answer was `0x11` your flag would be `picoCTF{17}`. Download the assembly dump `here`.


## Hints (if any)
1. Don't tell anyone I told you this, but you can solve this problem without understanding the compare/jump relationship.
2. Of course, if you're really good, you'll only need one attempt to solve this problem.

## Approach
Similar to the [Bit-O-Asm-3](./Bit-O-Asm-3.md) challenge, this is little complex. 

As done in that challenge, firstly we check the contents of the challenge file.

![File content](./img/bit%200%20asm%204%201.png)

Then we open up the file content in a text editor and start computing the required value.

![Content in text editor](./img/bit%200%20asm%204%202.png)

After computing the instructions, we get `eax` as `0x9fdb5` or `654773` in decimal which is our flag.

![solved instructiona](./img/bit%200%20asm%204%203.png)

## Flag
picoCTF{654773}