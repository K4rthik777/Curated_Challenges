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

# 2. Nutrela Chunks

>Description:

Two philosophers peer into the networked abyss and swap a secret. Use the secret to decrypt the Abyss’ RAwR and pull your flag from the void

## Solution:

- I viewed the packects of capture file in wireshark and in the PSH , ACK flag in TCP type protocols and found a conversation and found a ciphertext and the key . then i used cyclic XOR decryption to get the flag.

  The XOR ciphertext:

  <img width="1910" height="964" alt="Screenshot 2025-11-30 151355" src="https://github.com/user-attachments/assets/77cb938f-c781-41b6-9875-aa306acdb46b" />

  The key for the ciphertext:
  <img width="1904" height="862" alt="image" src="https://github.com/user-attachments/assets/43fa7e29-427e-4f95-b637-7d34113b9744" />


## Flag:

```
flag{1_533_tH3_voID_4nd_th3_vO1D_5335_m3_b4ck_0r_wA5_it_4_c4Mu5_qUot3_oR_w45_it_7h3_d3f1n171On_0f_7h3_R4Rp_prOtOc0L}
```

## Concepts learnt:

- I learned how data can viewed in the tcp packets with PSH and ACK flags.

## Notes:

- i kept trying to find anything useful within each packets.
  
## Resources:

-  ()
