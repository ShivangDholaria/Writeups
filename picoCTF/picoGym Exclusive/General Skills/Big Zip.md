# First Find

## Overview

Points: 100

Category: General Skill

## Description
Unzip this archive and find the flag.

    Download zip file


## Hints
1. Can grep be instructed to look at every file in a directory and its subdirectories?

## Approach

This is kind of an extension to the previous challenge [First Find](/picoCTF/picoGym%20Exclusive/General%20Skills/First%20Find.md). Here we need to find the flag text from all the files given in all the subdirectories respectively. To do this, we can use ```grep``` (Note: ```grep``` is a case sensitive tool. So "picoctf" and "picoCTF" will be considered as different strings). Since we already know the flag format, we can easily get the whole flag.

The command to do so is really simple

```bash
grep -r "pico" /path-to-unziped-directory
```

![path to the challenge file](img/Big%20zip%201.png)

Use ``` man grep``` to see the manual page for grep and learn more on how to use it. 

Then ```cat``` out the contents of the file to get the flag

## Flag
picoCTF{gr3p_15_m4g1c_ef8790dc}