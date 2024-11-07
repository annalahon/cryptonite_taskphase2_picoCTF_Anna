# Absolute Paths

**Flag:** picoCTF{7h3_p47h_70_5ucc355_e5a6fcbc}

**Description:** 
Can you get the flag?
We know that the website files live in /usr/share/nginx/html/ and the flag is at /flag.txt but the website is filtering absolute file paths. Can you get past the filter to read the flag?
Additional details will be available after launching your challenge instance.

**Approach:** Since the challenge is called "forbidden Paths", where it says that the website is filtering absolute file paths, we can easily figure out that it has something to do with the required file's absolute path. We are given where the website file lives and the name of the file.
Using ```../../../../``` since there are four names in the given path, we can access  `/flag.txt`'s absolute path and receive the flag by using the read button.
![image](https://github.com/user-attachments/assets/b1172560-ebb1-48e4-8fb8-c6cf37293352)
![image](https://github.com/user-attachments/assets/7daecde5-682e-4a2d-80c5-53ae8f479a85)

**Learnings:** Use of absolute paths without typing out all the folders/directories.

**Incorrect methods used:** Tried typing out given path and then the file path but that did not work.
