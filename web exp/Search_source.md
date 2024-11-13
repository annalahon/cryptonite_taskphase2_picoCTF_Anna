# Search Source

**FLAG:** picoCTF{1nsp3ti0n_0f_w3bpag3s_8de925a7} 

**Description:**
The developer of this website mistakenly left an important artifact in the website source, can you find it?
The website is here.

**Hints:** 
How could you mirror the website on your local machine so you could use more powerful tools for searching?

**Approach:** 
1. Opened the website and went through the source code for a bit but i realized that it was too lengthy and would take forever to go 
through manually. So i read the hint again and searched up how to mirror websites onto our laptop. That led me to the `wget` command
which can be used on ubuntu to download all the files from an html site onto our laptop.

2. I first checked if the command was installed by using `wget --help` command and it gave me the various arguments that can be used with this command.
Then i used the ```wget -mpEk http://saturn.picoctf.net:56104/``` command which i learnt from this [link](https://www.howtogeek.com/how-to-copy-a-whole-website-to-your-computer-using-wget/) but this did not work at first.
After reading through the help page, i tried using these arguments separately which seemed to work : ``` wget -m -p -E -k http://saturn.picoctf.net:56104/```.
It gave me this output which showed the downloading of the files in the site:
![image](https://github.com/user-attachments/assets/ca29f065-ebc2-4811-a869-e1041e7eac04)
and various other files got downloaded just like this.

3. Next i had to access the downloaded files, which was available on the same site as given above. The files were available at `\\wsl.localhost\Ubuntu-22.04\root\saturn.picoctf.net56104`.
I opened them in word which made it look like this
![image](https://github.com/user-attachments/assets/93c2d4ad-bf38-43d7-a275-05ec98c3e4b0)
with too many characters to search manually. So i used the **find** function and put in **pico** as the word to be searched.
It gave me the flag in the **style** document:
![image](https://github.com/user-attachments/assets/21ef8707-e537-47a9-b745-a76908464421)

**Learnings:**
1. I learned that we can mirror websites.
2. How to access files downloaded through wsl

**Resources:**
1. [LINK](https://www.howtogeek.com/how-to-copy-a-whole-website-to-your-computer-using-wget/) to learn how to use wget
