# format string 0

**Flag:** picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_ef312157}

**Description:** Can you use your knowledge of format strings to make the customers happy?
Download the binary here.
Download the source here.
Additional details will be available after launching your challenge instance.
Connect with the challenge instance here:
nc mimas.picoctf.net 50235

**Hints:** 
1. This is an introduction of format string vulnerabilities. Look up "format specifiers" if you have never seen them before.
2. Just try out the different options

**Approach:**
On connecting to the server, it gives us the question
![image](https://github.com/user-attachments/assets/3189474b-ff8f-4d94-b92e-956937eb83ee)
Now based on the first hint, i searched up about format specifiers and learnt that **%** is used to specify the format of what comes next. Using this, i tried putting `Gr$114d_Cheese` as the answer which led me to the next question
![image](https://github.com/user-attachments/assets/85e317be-b634-43bf-8ea1-8e1a62aa4d91)
As an answer to this, i once again tried the first option with % in it : `Pe%to_Portobello` which led me nowhere. 
Now following the second hint, i tried the other option : `Cla%sic_Che%s%steak` which gave me the flag.

**Learnings:**
Use of `%` as format specifier in C

**Resources:**
Using this [link](https://www.geeksforgeeks.org/format-specifiers-in-c/) I learned about the format specifiers
