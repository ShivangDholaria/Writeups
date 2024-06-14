# ASCII FTW

## Overview

Points: 100

Category: Reverse Engineering

## Description
This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program. You can download the file from here.

## Hints (if any)
1. The combined range of hex-ascii for English alphabets and numerical digits is from 30 to 7A.
2. Online hex-ascii converters can be helpful.

## Approach

Let's download the file and see what the file is actaully.

![file info](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/img/ascii%20ftw%201.png)

Since it's an ELF file, let's run the file and see how it works!

![file run info](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/img/ascii%20ftw%202.png)

Since the challenge is a reverse engineering challenge, I used ghidra to see the decompiled code and then work from there. Install ghidra in your system and open the file in it.

![ghidra](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/img/ascii%20ftw%203.png)

Look for the main(libc_start_main if main is not present) function in the symbol tree.

![main function](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/img/ascii%20ftw%204.png)

We see `lVar1` variable in the decompiled code. On selecting it, we are taken to where it is actually present in the disassembled code. From there we can se `0x70` value below the selected line. Now if we convert that value to char, we get it as `p`.

![hex to char](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/img/ascii%20ftw%205.png)

By this I infered that the whole flag is encoded in hex. So select all those lines that have the `0x` values in it and paste it in another file.

![hex to char](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/img/ascii%20ftw%205.png)

We clean-up the file with only the hex values remaining and then run the python code to get the flag.

![cleaned up file](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/img/ascii%20ftw%206.png)

![hex to char](/picoCTF/picoGym%20Exclusive/Reverse%20Engineering/img/ascii%20ftw%207.png)


We can just clean that file and write a python script that can print out the flag for us!

## Flag
picoCTF{ASCII_IS_EASY_3CF4BFAD}
