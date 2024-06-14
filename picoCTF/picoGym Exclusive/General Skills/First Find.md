# First Find

## Overview

Points: 5
Category: General Skill

## Description
Unzip this archive and find the file named 'uber-secret.txt'

    Download zip file


## Hints

No hints available for this challenge.

## Approach

This is an easy challenge. We will need only 2 commands to solve this: ```find``` and ```unzip```

```unzip``` will unzip the archive, which contains a file named 'uber-secret.txt'

For this challenge the command will look like

```bash
find /path-to-unziped-directory -name "uber-secret.txt" 
```

Use ``` man find``` to see the manual page for find and learn more on how to use this tool. 

![path to the challenge file](img/first%20find%201.png)

Then ```cat``` out the contents of the file to get the flag

## Flag
picoCTF{f1nd_15_f457_ab443fd1}