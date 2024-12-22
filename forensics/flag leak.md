# flag leak

**Flag:** picoCTF{qu1t3_a_v13w_2020}

**Description:**
We found this file. Recover the flag

**Hints:**
Weird that it won't display right...

**Approach:**
I tried opening the downloaded file with `file /mnt/c/users/anna/downloads/tunn3l_v1s10n` but it just gave me 
![image](https://github.com/user-attachments/assets/09f76c48-bd06-436f-9601-486f174f4479)
so i searched up how to get the details of the file and i used  `exiftool /mnt/c/users/anna/downloads/tunn3l_v1s10n` which gave me ![image](https://github.com/user-attachments/assets/59abc436-406a-4349-a6b2-913ee7f8c9c9)
Here, it showed the file type as *BMP* and MIME type as *image/bmp* so i tried doing a little more research and got the hex values using `hexedit`
![image](https://github.com/user-attachments/assets/60649b04-9d12-440f-950c-cd1a73a3b935)
And after researching i changed the infoheader hex values from `BA D0 00 00` to `28 00 00 00` to give us the necessary 40 bytes. When i opened, i got an image with a decoy flag:
![image](https://github.com/user-attachments/assets/a6842bf4-e725-4717-949a-90958b611a38)
Now i did more research and figured out that the actual file size was bigger than what was actually being shown, so i tried 2 different methods: changing the width and height.
Changing the width just distorted the image so i searched up on how to change the height. I learnt that i had to change the `32 01 00 00` set to `32 03 00 00` as so
![image](https://github.com/user-attachments/assets/1097156b-cb5c-48b9-9be6-d61580032a0d)
which gave me the image with the flag
![image](https://github.com/user-attachments/assets/3a200638-7b6a-4768-a4d1-c8cd90f6bb05)

**Resources:**
1. Used this [link](https://medium.com/sysf/bits-to-bitmaps-a-simple-walkthrough-of-bmp-image-format-765dc6857393) to learn about a bmp image.
2. Used this [link](https://www.networkworld.com/article/971883/using-linux-hexedit-and-xxd-commands-to-view-and-modify-binary-files.html) to learn how to change the hex values
