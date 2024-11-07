# buffer overflow 0

**Flag:** picoCTF{ov3rfl0ws_ar3nt_that_bad_c5ca6248}
  
**Description:** Let's start off simple, can you overflow the correct buffer? The program is available here. You can view source here.
Connect using:
`nc saturn.picoctf.net 64540`

**Hints:**
1. How can you trigger the flag to print?
2. If you try to do the math by hand, maybe try and add a few more characters. Sometimes there are things you aren't expecting.
3. Run `man gets` and read the BUGS section. How many characters can the program really read?

**Approach:** They had provided the source code and the program. Going throught the program didnt help much so I went through the source code for some clue related to hint no.1.
I was looking for a part of the program where the flag was getting printed and what caused it to print. There i saw the `sigsegv_handler` function and in another function there 
was a variable being initialized as `char buf2[16];` which meant that the variable buf2 had a size of 16 characters and takes input from the user. By typing any number with no. of 
digits greater than 16, it overflows and prints out the flag.
![image](https://github.com/user-attachments/assets/7324f652-09cf-433c-9b36-33e7c150116a)

**Learnings:**
I did not know what a 'Signal Handler' in C was so I searched it up to find out its functionality.
Also learnt about buffer overflowing.

**Incorrect methods:**
Inputted 16 characters which cause the program to exit instead of giving me the flag.

**Resources:**
Used this [link](https://www.geeksforgeeks.org/signals-c-language/) to learn about signal handlers.
