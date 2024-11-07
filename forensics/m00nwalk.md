# m00nwalk

**Flag:** picoCTF{beep_boop_im_in_space}

**Description:** Decode this message from the moon.

**Hints:** 
1. How did pictures from the moon landing get sent back to Earth?
2. What is the CMU mascot?, that might help select a RX option.

**Approach:**
The challenge gave us an audio `.wav` file. From the first hint, after research, i found that pictures from the moon were received back on earth by **QSSTV** which is a utility for dealing with slow scan television signals.
I searched up ways for downloading it. It gave me the command `apt-get install qsstv`. After that I ran the PulseAudio control GUI by running `pavucontrol &` and `qsstv &` to open both applications simultaneously.
Then we had to create a PulseAudio module by the command  `pactl load-module module-null-sink sink_name=virtual-cable` which we later connect to qsstv. Once the module is created,
it prints its id in the terminal.
![image](https://github.com/user-attachments/assets/b3232bf5-a7f1-4d36-b7b5-b542792fef29)
Then we open the PulseAudio gui and make sure that the null output device exists. After this we need to make sure that qsstv has PulseAudio selected
for the input and output device. 
![image](https://github.com/user-attachments/assets/73557296-4d87-4895-87ae-42c7d9889401)
This makes sure that the audio played by PulseAudio gets played on qsstv to be converted to an image. A last setup needs to be made in the pavucontrol window,
where we make sure that qsstv records from the **Null Output**.
![image](https://github.com/user-attachments/assets/422160e1-bdc7-4e1c-b045-73280ba44f2d)
 After this we start receiving on qsstv, set the mode to **Scottie 1** which we got from hint no.2, run `paplay -d virtual-cable /mnt/c/users/anna/downloads/message.wav`
and then the image gives us the required flag.

![image](https://github.com/user-attachments/assets/6de645ac-4a50-4a40-a83a-382826d97bf3)

**Learnings:**
I learnt how to convert an audio file to an image through qsstv.

**Resources:**
I learnt how to use qsstv through this [link](https://ourcodeworld.com/articles/read/956/how-to-convert-decode-a-slow-scan-television-transmissions-sstv-audio-file-to-images-using-qsstv-in-ubuntu-18-04)
