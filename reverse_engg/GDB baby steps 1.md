# GDB baby steps 1

**Flag:** picoCTF{549698}

**Description:** Can you figure out what is in the eax register at the end of the main function? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Disassemble this.

**Hints:** 
1. gdb is a very good debugger to use for this problem and many others!
2. main is actually a recognized symbol that can be used with gdb commands.

**Approach:**
Downloaded the file and cd to the downloads directory in linux. Since the first hint mentions gdb,
i searched up on what it is and how to use it in reverse engineering. From there, I installed it and
opened the **debugger0_a** file.
![image](https://github.com/user-attachments/assets/c6aaaf22-25fb-4367-a137-d3188ee8e4e1)
After this, the website gives a command of ```set disassembly-flavor intel``` which set the disassembled code
in the intel syntax which is usually preferred by people.
In the second hint, it mentions the `main` symbol and so I run ```disassemble main``` which gives me this:
![image](https://github.com/user-attachments/assets/f2010c20-1220-4275-891c-09265d5953c0)
In this, i notice the `eax` register which has a value of `0x86342`. I put this in a hexadecimal->decimal converter
and get the value `549698`.
![image](https://github.com/user-attachments/assets/6e510488-81e0-41cc-82c0-b84d0dab58b8)


**Learnings:**
1. Use of GDB (GNU Debugger)
2. Disassembly of programs

**Resources:**
1. Learnt how to use GDB in reverse engineering through this [link](https://www.retroreversing.com/tutorials/gdb-reversing)
2. Learnt about eax register through this [link](https://electronicsreference.com/assembly-language/assembly-language-registers/)
3. 
