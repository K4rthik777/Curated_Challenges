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
