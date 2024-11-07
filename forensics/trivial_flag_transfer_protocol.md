# trivial flag transfer protocol

**FLAG:** picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

**Description:** Figure out how they moved the flag.

**Hints:** What are some other ways to hide data?

**Approach:**
On opening the file through linux, there was a mention of **Wireshark** so i searched up what it was and learned that it was a network analyzer which captures network traffic and 
lets us access it. So I downloaded it and opened the `tftp.pcapng` file on it. On that, a lot of the traffic had `TFTP` as the protocol and that was also the name of the file, so i searched up what it stood for.
![image](https://github.com/user-attachments/assets/51f4d4b6-c76a-476f-97c5-d44839bb2c10)
It gave me results of **Trivial file transfer protocol** and even the challenge was a wordplay based on this. I then searched up how to access these files on wireshark which led me to the export objects tab
where i could download the required files.
![image](https://github.com/user-attachments/assets/554d9645-ff5d-451d-9795-60cb1269141b)
I first opened the only text file there - `instructions.txt` which had an encrypted message in it - `GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA`. 
From little previous knowledge, I used cryptii to ROT13 it and got the text `TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN`.
Applying spaces appropriately, we get `TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER. FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN`.
This led me to the next file `plan ` which only had a file extension. After opening that, there was another encrypted message in it - `VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF`.
By applying the same logic as before, I got the message - `I USED THE PROGRAM AND HID IT WITH-DUEDILIGENCE. CHECK OUT THE PHOTOS`.
Next i downloaded the photos and noticed a new extension type that i had never used before `.bmp`. I researched on this and found that they were images/audio files used to hide some sort of data.
There was another program file there left `program.deb`. I tried to find out what type of file it was and it said it was a **Debian binary package**. 
![image](https://github.com/user-attachments/assets/4a96f23e-075f-455d-8262-ab3fdccdc82e)
From previous challenges,I thought of installing this package by using `sudo apt install /mnt/c/users/anna/downloads/program.deb`
![image](https://github.com/user-attachments/assets/13aaca2e-e899-453a-ad65-7805198e55d6)
Here i faced an issue with something called **steghide** and i didnt know what it was, so i searched it up and found that it was a way of hiding data in image and audio files just like .bmp files that we had.
So i installed that too and searched up how to extract the hidden data using it, where i found `steghide extract -sf /file.ext -p pass` where pass was the password, which i guessed was **DUEDILIGENCE**
in this challenge due to the hyphen in the decrypted text.
One by one i tried extracting data from the pictures. The first two failed to give any data, but on the third one, it said it printed the flag to the flag file. So i catted the flag file and received the flag.
![image](https://github.com/user-attachments/assets/a0995047-4fce-4244-ab1d-830b88ac63f2)

**Learnings:**
1. wireshark application and use of network analyzers
2. .bmp files and how to extract data from them.
3. what a steghide was and how to use it.

**Incorrect methods:**
1. Had to try multiple ways of decrypting before getting to ROT13
2. not using the password while trying to extract data from .bmp files

**Resources:**
1. This [link](https://pupuweb.com/how-hide-secrets-images-audio-files-linux-steghide/#Extract_Data_from_an_Image_Using_Steghide) helped me learn how to use steghide.
2. This [link](https://fileinfo.com/extension/bmp) helped me learn about .bmp files.
3. This [link](https://www.wireshark.org/docs/wsug_html/) showed me how to use wireshark and access files through it.
