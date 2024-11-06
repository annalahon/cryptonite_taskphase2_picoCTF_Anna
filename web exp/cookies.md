# cookies

**Flag: picoCTF{3v3ry1_l0v3s_c00k135_bb3b3535}**

**Method:**
Since they gave us a website, i first typed in the prompt of `snickerdoodle` in the search bar, it says 'I love snickerdoodle cookies!' which wasn't of too much help. 
Since most website based CTF's use the inspect tool, I used it too to check out the cookies on the page while being on the default page.
In that there was one cookie with the value 0. I noticed that this value could be edited, so i started typing out numbers from 1 increasing them till i reached 18 and the flag was displayed on the webpage.
![image](https://github.com/user-attachments/assets/772d2ed9-b9b8-4395-b6f7-c407c5294e8d)

**Learnings:**
I didnt know how to access a website's cookies through the inspect page before, but fooling around led me to applications under which it was available.

**Incorrect methods:**
Tried searching for other clues in the inspect page code, thought that the flag might be contained in that.

**References:**
Previously, I had taken part in Oasis CTF in which they had a challenge where we had to use inspect so that helped me here.
