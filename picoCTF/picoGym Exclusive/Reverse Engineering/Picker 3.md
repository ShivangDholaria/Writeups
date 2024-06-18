# Picker 3

## Overview

Points: 100

Category: Reverse Engineering

## Description
Can you figure out how this program works to get the flag? Connect to the program with netcat: 

`$ nc saturn.picoctf.net 57780`

The program's source code can be downloaded `here`.

## Hints (if any)
1. Is there any way to modify the function table?

## Approach
This challenge was a tricky one. Here, there is a lot happening under the hood. 

![code intro](./img/Picker%203%201.png)

We see that we can access 4 function on runtime. Using these functions, we have to get the flag. So lets review the code and see how its structured.

![source code](././img/Picker%203%202.png)

![source code](././img/Picker%203%203.png)

![source code](././img/Picker%203%204.png)

There is something interesting here, we can see a global variable `func_table` declared in the code. And that variable is the one that prints the functions that can be used. So what if we can somehow rewrite the value of that variable in such a way that we can execute the `win` function?

We can do so by calling the `write_variable` function and passing our own value to it. But there's a catch too, the `check_table` function ensures that length of the table should be of a specific size which is `32 * 4 = 128` characters.

So we need a string that has a length of 128 which contains `win` in it. To do so, we just do the following in python"
`print('win' + ' ' + 'a' * ((32 * 4) - 1 - 3))`

We then get our payload:
`win aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa`

Now when we run the program, we first select the write_variable function and write our payload into the `func_table` function. After which, when we enter 1, we get our flag.

![writing into variable](./img/Picker%203%206.png)

And now lets unhex the hexed flag:

![unhex flag](./img/Picker%203%205.png)

## Flag
picoCTF{7h15_15_wh47_w3_g37_w17h_u53r5_1n_ch4rg3_c20f5222}