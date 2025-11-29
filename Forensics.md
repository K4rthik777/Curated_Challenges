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

