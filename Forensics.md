# 1. Hide and Seek

>Description:

Sakamoto’s at it again with a game of hide and seek, but this time, it’s not with Shin or his daughter. An old friend hid some secret data in this image. Can you find it before the others do?

Hint:
Even in retirement, Sakamoto never loses at hide and seek. Maybe stegseek can help you keep up.

## Solution:

- i used the stegseek tool with the argument --crack with sakamoto.jpg file and the wordlist rockyou.txt along with the output file cracked.txt

```bash
stegseek --crack sakamoto.jpg rockyou.txt cracked.txt
```
<img width="1007" height="207" alt="image" src="https://github.com/user-attachments/assets/4d441669-d7cc-4410-81d6-92a0ed3e110d" />


## Flag:

```
nite{h1d3_4nd_s33k_but_w1th_st3g_sdfu9s8}
```

## Concepts learnt:

- I learned how to use stegseek to get encrypted info from images. 

## Notes:

- i kept trying the stegseek command but it was failing to open the rockyou.txt wordlist file. I found out that it was not default installed in ubuntu so i had to install that manually from the github

## Resources:

-  (https://github.com/RickdeJager/stegseek)
-  (https://www.youtube.com/watch?v=L_dKHVxerVo)

# 2. Nutrela Chunks

>Description:

One of my favorite foods is soya chunks. But as I was enjoying some Nutrela today, I noticed a few chunks weren’t quite right. Seems like something’s off with their structure. Could you help me fix these broken chunks so I can enjoy my meal again?

## Solution:

- I viewed the byte structure of the png file and found the incorrect PNG signature chunk,IHDR chunk, IDAT chunk. So i corrected those to get the image

  The original byte structure of nutrela.png

  <img width="786" height="737" alt="image" src="https://github.com/user-attachments/assets/e0cbf220-1c35-488c-a5a9-78a125ac4766" />

  The changed byte structure

  <img width="821" height="727" alt="image" src="https://github.com/user-attachments/assets/b0d88d94-0e01-4ed2-beaf-ed35179b89e3" />


## Flag:

```
nite{nOw_yOu_knOw_abOut_PNG_chunk5}
```

## Concepts learnt:

- I learned what are the different chunk in the png byte structure. 

## Notes:

- i kept trying to change the IDAT and IEND chunks so the image i was getting was a blank image.
## Resources:

-  (https://www.google.com/url?sa=i&url=https%3A%2F%2Fstackoverflow.com%2Fquestions%2F54845745%2Fnot-able-to-read-ihdr-chunk-of-a-png-file&psig=AOvVaw2W4g_B_yYExUdP_7h1twAl&ust=1764576438481000&source=images&cd=vfe&opi=89978449&ved=0CBUQjRxqFwoTCPCX4M-1mZEDFQAAAAAdAAAAABAM)

# 3. RAR of the Abyss 

>Description:

Two philosophers peer into the networked abyss and swap a secret. Use the secret to decrypt the Abyss’ RAwR and pull your flag from the void

## Solution:

- I viewed the packects of capture file in wireshark and in the PSH , ACK flag in TCP type protocols and found a conversation and found a .rar file so i extracted that using the password given in the following packets to get the txt file containing the flag.

  The .rar file in the tcp packet:

  <img width="1910" height="964" alt="Screenshot 2025-11-30 151355" src="https://github.com/user-attachments/assets/77cb938f-c781-41b6-9875-aa306acdb46b" />

  The password for the .rar file:
  <img width="1904" height="862" alt="image" src="https://github.com/user-attachments/assets/43fa7e29-427e-4f95-b637-7d34113b9744" />


## Flag:

```
nite{thus_sp0k3_th3_n3tw0rk_f0r3ns1cs_4n4lyst}
```

## Concepts learnt:

- I learned how data can viewed in the tcp packets with PSH and ACK flags.Also how file can be extracted from the tcp packets.

## Notes:

- i kept messing up the .rar file extraction somehow so it wasn't opening in the software.
  
## Resources:
-(https://stackoverflow.com/questions/40743773/how-to-extract-raw-data-from-tcp-packets-using-wireshark)

# 4. NineTails

>Description:

>Looks like I got a little too clever and hid the flag as a password in Firefox, tucked away like one of NineTails’ many tails. Recover the "logins" and the "key4" and let it guide you to the flag.

Hint:
I named my Ninetails "j4gjesg4", quite a peculiar name isn't it? 

## Solution:

- I extracted given .rar file to get an .ad1 file and then i extracted this ad1 file using ftk imager. In this i searched for all j4gjesg4 profiles in firefox folders. I found the logins.json and keys.db files. Then i used the firefox decrypt python script tool to get the saved passwords.So i joined the passwords to get the flag.

The ftk imager showing the logins.json and key4.db:
<img width="1354" height="656" alt="image" src="https://github.com/user-attachments/assets/aec0bc6e-257a-442b-a5da-5a15714e097c" />

The python script usage:

<img width="1109" height="567" alt="image" src="https://github.com/user-attachments/assets/d1361b9f-0269-4315-b3e0-d63faf12ee7f" />

## Flag:

```
GCTF{m0zarella_f1ref0x_p4ssw0rd}
```

## Concepts learnt:

- I learned how to view ad1 files and how to decrypt the saved passwords in the logins.json using python decryption script.

## Notes:

- i kept messing up the extracting of ad1 file using wrong software and used some other tool for decrypting the passwords but it didn't work.
  
## Resources:
-()

# 5. Re:Draw

>Description:

>Her screen went black and a strange command window flickered to life, lines of text flashed across before everything went silent. Moments later, the system crashed. By sheer luck, we recovered a memory dump. 

Note: There are three stages to this challenge and you will find three flags.

What we know: just before the crash, a black command window flickered across the screen, something in its output might still be visible if you dig through memory. She was drawing when it happened, and remnants of a painting program linger, which could reveal more if inspected in the right way. Finally, a mysterious archive hides deeper in memory, likely holding the last piece of her work.

Hint:Learn up on volatility 2 and its various plugins and what they are used for.
 
## Solution:
Initially i unziped the 7zip file to get a .raw file and then i tried access it through volatility tool in python and tried to follow the clues given in the description.By using the volatility tool i got the info about this .raw with this command ```volatility -f MemoryDump_Lab1.raw imageinfo``` and it' s version seems to be Win7SP1x64 
For the stage 1, i accessed the processes list and tried to find any process that poped up as mentioned in the description using this command ```bash volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x64 pslist```. Then i tried checking the consoles this time using this command ```bash volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x64 consoles ``` and found a encoded text in base64 and decoded it to get the first flag.
For the stage 2, i extracted the mspaint memory as .dmp using the command ```bash volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x64 memdump -p 2424 -D ./ ``` and then i tried viewing this file by changing its extension .data and opening in gimp tool . There  i set the offset to 500 and tried different combinations for width and height to get a readable image and at height = 1230 and width = 2234 i got an inverted mspaint image with flag written in it.

<img width="903" height="574" alt="Screenshot from 2026-01-09 14-22-57" src="https://github.com/user-attachments/assets/65cb308f-f657-46a0-85ee-b02836e48ae0" />

For the stage 3 ,  i extracted the winrar memory into .dmp file ```volatility -f ../MemoryDump_Lab1.raw --profile=Win7SP1x64 memdump -p $PID -D winrar_memory/ ``` and then then i scanned the memory dump for archives and transfered their names to a .txt file.
```
volatility -f ../MemoryDump_Lab1.raw --profile=Win7SP1x64 filescan > all_files.txt
grep -i "\.rar\|\.zip\|\.7z\|\.tar\|\.gz\|\.cab" all_files.txt | head -20 > archive_files.txt
cat archive_files.txt
```
Then i used this txt file to extract that file and got a .dat file. But upon viewing the bytes of the file in hexeditor it was clear that this was rar file. So i changed the extension to .rar and tried extracting this file and it asked for the NTLM hash of Alissa Simpson user's password so i tried the each hash and it opened for the second hash to give the flag3.png
```
volatility -f MemoryDump_Lab1.raw --profile=Win7SP1x64 hashdump > all_hashes.txt
grep -i "alissa\|simpson" all_hashes.txt
```

<img width="500" height="500" alt="flag3" src="https://github.com/user-attachments/assets/1da542e8-9922-4f15-9cd1-1ea2ce323225" />


## Flag:
Stage1 - ```flag{th1s_1s_th3_1st_st4g3!}```

Stage2 - ```flag{Good_Boy_good_girl}```

Stage3 - ```w3ll_3rd_stage_was_easy```

## Concepts learnt:

- I learned how volatility can be used to analyse, scan and extract memory dumps(.raw,.dmp) and allows to view and investage through all processes and even individual application activity can be observed.

## Notes:

- i kept trying to using the entire pc memory dump in the gimp but it was supposed to be the .dmp dile of the mspaint that had to opened instead. Also i kept going after wrong .rar archives which were corrupted and couldn't open.
  
## Resources:
-(https://github.com/volatilityfoundation/volatility)

