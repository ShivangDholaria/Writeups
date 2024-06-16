# GDB baby step 3

## Overview

Points: 100

Category: Reverse Engineering

## Description

Now for something a little different. `0x2262c96b` is loaded into memory in the `main` function. Examine byte-wise the memory that the constant is loaded in by using the GDB command `x/4xb addr`. The flag is the four bytes as they are stored in memory. If you find the bytes `0x11 0x22 0x33 0x44` in the memory location, your flag would be: `picoCTF{0x11223344}`.

Debug `this`.

## Hints (if any)
1. You'll need to breakpoint the instruction after the memory load.
2. Use the gdb command `x/4xb addr` with the memory location as the address `addr` to examine. [GDB manual page](https://ftp.gnu.org/old-gnu/Manuals/gdb/html_node/gdb_55.html).
3. Any registers in `addr` should be prepended with `$` like `$rbp`.
4. Don't use square brackets for `addr`.
5. What is [endianness](https://en.wikipedia.org/wiki/Endianness)?

## Approach

Same as previous challenge, lets debug the executable.

But first, the basic checks. Lets find what kind of file it is and if it produces any output.

![file type](./img/gdb%20baby%20step%203%201.png)

![file output](./img/gdb%20baby%20step%203%202.png)

Now opening it up in `gdb`, lets see if the main function is present and disassemble it. But just before this, we set the disassembly style(flavor) to intel so its understandable.

![list of functions](./img/gdb%20baby%20step%203%203.png)

```bash
set disassembly-flavor intel
```

![disassembled main](./img/gdb%20baby%20step%203%205.png)

Lets set a breakpoint just before the program completes its execution and find out what value is present in the register `eax`.

To set a breakpoint, we write the following command:
```bash
break *address
```
Here, the memory address is written in blue like `0x0000000000401106`. Since, we dont need all the leading zeroes, we can discard them.

So we set the break point at address `0x40111f`, and run the code. We will hit the breakpoint when it reaches the line where we have placed our breakpoint.

Once we hit the breakpoint, we will get the following message:

![breakpoint hit](./img/gdb%20baby%20step%203%206.png)

Lets see what the value in the register `eax` is:

![eax value](./img/gdb%20baby%20step%203%207.png)

But for this challenge, we need the address value and not the actual value present in that memory address. So, we if we try to find out what is present in the address `0x2262c96b`, we will get the following message:

![Cannot access memroy address](./img/gdb%20baby%20step%203%208.png)

There must me something wrong with out approach, so lets revist the disassembled main function.

We see that firs the value is being moved to the some address `rbp - 0x4` and then in register `eax`, that value present is put in it.

So, we need to find out the memory location `rbp - 0x4`. To do this we type the command we found in the discription of the challenge:

```bash
x/4xb address
```

Since `rbp` is a special type of register, we need to `$` as stated in the description. 

```bash
x/4xb $rbp-0x4
```
Now we get the actual address where the value `0x2262c96b` is present.

![Address value](./img/gdb%20baby%20step%203%209.png)

And there's our flag!

## Flag
picoCTF{0x6bc96222}