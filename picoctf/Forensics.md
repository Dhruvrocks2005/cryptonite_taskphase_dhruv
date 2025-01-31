# Forensics - Mandatory Challenges

## Trivial Flag Transfer Protocol

Opened the given file using `Wireshark`.

![image](https://github.com/user-attachments/assets/14420fdf-dc56-496d-a9ae-7092434f1aea)

![image](https://github.com/user-attachments/assets/b6be4dd4-768b-487d-9de2-018428cc9c58)

The following files were extracted: `instructions.txt`, `plan`, `program.deb` and 3 images which seem to be unrelated.

instructions.txt:

```
GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA
```

This turned out to be simple ROT13 cypher.

```
TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN
```

The `plan` file conatined this:

```
VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF
```

This also turned out to be ROT13.

```
IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS
```

I then ran `sudo dpkg -i program.deb` and found that it is steghide but it was broken/obsolete so I used an online tool instead - https://futureboy.us/stegano/decinput.html 

The password was `DUEDILIGENCE` as given in `plan`. I ran all 3 images through the Steganographic Decoder and found the flag in `picture3`.

![image](https://github.com/user-attachments/assets/d1b04941-61b4-4d76-931b-4c59d95b18f3)

**Flag:**

```
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```

**Resources Used:**
- Wireshark
- https://futureboy.us/stegano/decinput.html
- `Forensics in CTF's` playlist on `picoCTF` - https://play.picoctf.org/playlists/16?m=114
- https://play.picoctf.org/playlists/16?m=127
- https://www.youtube.com/watch?v=J-wgivK4X-A&t=9s&ab_channel=picoCTF%2CCarnegieMellonUniversity

## tunn3l v1s10n

Received a file named `tunn3l_v1s10n`, which doesn't open. Flag not found upon searching in text editor.

ran `file tunn3l_v1s10n`

![image](https://github.com/user-attachments/assets/96f06b54-454e-44dd-bb04-e739830a7154)

ran `exiftool tunn3l_v1s10n`

![image](https://github.com/user-attachments/assets/26c0d282-3941-4325-bf54-1b390e5c055f)

```
File Type: BMP (bitmap)
Image Width: 1134
Image Height: 306
Image Length(size): 2893400
```

Tried to open the file after changing the file extention to `.bmp` but to no avail.

![image](https://github.com/user-attachments/assets/3cb57bc1-d3df-4195-87e4-a4e6eb7e6272)

Opened the file in a hex editor (https://hexed.it/) to check and fix file header.

![image](https://github.com/user-attachments/assets/090a308d-ed2b-4ee6-a28b-29c3cc13c1ff)

Matched it with the required format and found discrepancies.

![image](https://github.com/user-attachments/assets/41855c43-3bd3-4df1-988e-4a88e9a44d41)

The DIB header should be `28 00 00 00`	(40 bytes). Replaced `BA D0` by `28 00`, and saved the image with a BMP extension(.bmp).

![image](https://github.com/user-attachments/assets/d4cecdc6-edd7-4084-808c-93ac83189f5c)

Did not find the correct flag so something is still wrong.

![image](https://github.com/user-attachments/assets/45c8651f-462d-4925-bc1a-6dd70bdfc1c7)

I tried to modify the `Offset where the pixel array (bitmap data) can be found`. I changed it to `36 00 00 00` (54 bytes) like in the example.

![image](https://github.com/user-attachments/assets/566250c6-f880-488d-8622-cf57395e95c6)

The image was still incomplete.

![image](https://github.com/user-attachments/assets/9f557941-d19a-46d8-a2bc-b7ccf9925c1e)

Image should be bigger-image height seems less.

Number of bits per pixel = 24 bits = 3 bytes

![image](https://github.com/user-attachments/assets/6047e4cb-2078-4f23-b5ba-77183089bcc0)

![image](https://github.com/user-attachments/assets/37352d79-3c1e-444a-a9cd-2c221871a493)

1134 * 306 * 3 ≠ 2893400

New image height = 2893400/(3*1134) = 850.5

(850)<sub>10</sub> = (0352)<sub>16</sub> 

Tried putting 850 as new image height:

![image](https://github.com/user-attachments/assets/8d885765-55fd-489d-ad9c-27085b34ad93)

This did not work because it is supposed to be in `little-endian` format (i.e. least-significant byte first).

![image](https://github.com/user-attachments/assets/766c0017-ba8e-4870-988c-bfc3c1846110)

It worked after fixing that.

![image](https://github.com/user-attachments/assets/0eb79963-66ed-44d2-9c08-efe411947699)

![image](https://github.com/user-attachments/assets/803ef8d7-6683-4b69-9752-59acee77e890)

**Reference:** https://en.wikipedia.org/wiki/BMP_file_format

**Flag:**

```
picoCTF{qu1t3_a_v13w_2020}
```

## m00nwalk

```
Description:
Decode this message from the moon. (A message.wav file is downloaded)

Hints:
1 How did pictures from the moon landing get sent back to Earth?
2 What is the CMU mascot?, that might help select a RX option
```

**Approach:**

The challenge involves decoding a message from a WAV file and references the moon landing's communication methods and the CMU mascot, which is Scotty.

1. **Moon Landing Communication**:
   - Moon landing signals were sent back to Earth using radio signals.
   - Audio files could be encoded with data like images or messages using techniques like **SSTV (Slow Scan Television)**, often used for transmitting images over radio frequencies.

2. **CMU Mascot**:
   - The mascot of Carnegie Mellon University (CMU) is Scotty, a Scottish Terrier. This  might imply using the `Scottie 1` mode.


### Decoding the SSTV Signal

Tried to use `RX-SSTV` to decode the signal but it wasn't working properly so had to switch to `QSSTV`.

Referred to this article for the procedure: [ How to convert (decode) a Slow-Scan Television transmissions (SSTV) audio file to images using QSSTV in Ubuntu 18.04](https://ourcodeworld.com/articles/read/956/how-to-convert-decode-a-slow-scan-television-transmissions-sstv-audio-file-to-images-using-qsstv-in-ubuntu-18-04)

In accordance with the above [procedure](https://ourcodeworld.com/articles/read/956/how-to-convert-decode-a-slow-scan-television-transmissions-sstv-audio-file-to-images-using-qsstv-in-ubuntu-18-04), commands used:

```
sudo apt-get install qt5-default libopenjp2-7-dev libpulse-dev libv4l-dev libasound2-dev libgtk-3-dev libfftw3-dev
sudo apt-get install pavucontrol
sudo apt-get install qsstv
qsstv
pactl load-module module-null-sink sink_name=virtual-cable
pavucontrol
paplay -d virtual-cable message.wav
pactl list short modules
pactl unload-module 22
```

- Installed required libraries.
- Installed pavucontrol.
  
![image](https://github.com/user-attachments/assets/e6b32eab-5290-4980-badf-1c6db7496a89)

- Installed qsstv.

-  Loaded a PulseAudio module `module-null-sink` and named it as `virtual-cable`.

![image](https://github.com/user-attachments/assets/337305c8-e7a2-471f-83fc-a8cc395ce772)

- Ran `pavucontrol`, and went to the `Output Devices` tab to verify that we have the `Null Output` device.
  
![image](https://github.com/user-attachments/assets/7a63a457-a9a6-4595-8c59-145372fbca58)

- Ran `qsstv` and specified that the QSSTV should capture the audio from our Null Output (in the pavucontrol GUI, in the `Recording` tab).
  
![image](https://github.com/user-attachments/assets/caeb1b8a-48e1-4690-8171-37ba621d4a6d)

- Selected `Scottie 1` as QSSTV's mode according to the `CMU Mascot` hint.

- Ran `paplay -d virtual-cable message.wav` to play the audio file.

![image](https://github.com/user-attachments/assets/e9b4b844-c2e4-4209-a544-40aadf47d3f2)

- Note: Bash was not allowing me to run commands while another was ongoing, so I had to use 3 terminals, one to launch `qsstv`, one to launch `pavucontrol` and one to play the audio file.

![image](https://github.com/user-attachments/assets/60f3a31d-f254-407c-bd92-b8873a2b9a2b)

![image](https://github.com/user-attachments/assets/28ab12c1-8e7d-46ff-8fed-6302ea7db1e6)

![image](https://github.com/user-attachments/assets/7946e123-9edc-4f58-b058-f17158ec6477)

- Played around with qsstv settings until I received the flag using trial and error.

- Needed to turn on `Auto Slant` mode, without which, incomplete parts of the image were forming instead of the complete image.

![image](https://github.com/user-attachments/assets/0f1ee667-8567-489a-a123-935f647455f9)

![image](https://github.com/user-attachments/assets/4e485d78-6e32-4f93-81fd-c03e36ebec5d)

- Resaturated audio in the system by unloading the `module-null-sink`.

![image](https://github.com/user-attachments/assets/09517117-692b-4ea5-b4bf-1a41b3fb553a)

![image](https://github.com/user-attachments/assets/cfc61553-117f-48f6-a2db-5947d25a8e47)

- The `virtual-cable` had an identifier of 22 in my case.
  
![image](https://github.com/user-attachments/assets/be6a0b76-1282-4dfb-9da8-f261bd5d337e)

**Decoded Image:**

![S1_20241212_195907](https://github.com/user-attachments/assets/ef103658-0792-4f4d-ae2d-fc457c22b6ef)

**Flag:**

```
picoCTF{beep_boop_im_in_space}
```

**Reference used:**  https://ourcodeworld.com/articles/read/956/how-to-convert-decode-a-slow-scan-television-transmissions-sstv-audio-file-to-images-using-qsstv-in-ubuntu-18-04

**Tangents:** 
- Tried to used `RX-SSTV` first but it didn't give me the desired output. Switched to `QSSTV` but the same thing happened there and that was when I realized that manually playing the audio would not work and upon further research, found out that we had to use `virtual-cable`/`null_sink`
- Some dependencies/libraries/packages for `qsstv` were broken or obsolete so time was wasted there
- Figuring out the correct settings for `QSSTV` (`Auto Slant` mode) also required a bit of trial and error

# Forensics - Extra Challenges

## Secret of the Polyglot

I opened the given PDF file and found half of the flag there.

![image](https://github.com/user-attachments/assets/bf495ad8-4523-469f-b7e2-f72206b27548)

```
1n_pn9_&_pdf_724b1287}
```

The given second part of the flag hints that the first part is related to PNG.

When I opened the given file in a text editor, I found out that it has elements of both a pdf and a png.

Then I opened the file in a hex editor, identified the PNG signature (starting with 89 50 4E 47 0D 0A 1A 0A and ending with 49 45 4E 44 AE 42 60 82), and isolated the PNG data from the rest of the PDF content.


![image](https://github.com/user-attachments/assets/7be3e1c4-ce8e-4251-8bed-1866728629f6)

The PNG contained the first half of the flag:

![hello](https://github.com/user-attachments/assets/3273e2cf-38c6-41b2-abf4-acdc02d23981)

![image](https://github.com/user-attachments/assets/617b13eb-dd1d-4f69-beb2-88aabd012402)

**Flag:**

```
picoCTF{f1u3n7_1n_pn9_&_pdf_724b1287}
```

## Enhance!

**Approach:** Found the flag when I opened the file in a text editor

![image](https://github.com/user-attachments/assets/0ea707cf-86b6-4d1a-9a47-92ad0ce4b044)

![image](https://github.com/user-attachments/assets/6d0191f9-aa21-4a4f-9c71-cb460e4f320b)

**Flag:**

```
picoCTF{3nh4nc3d_aab729dd}
```

## Glory of the Garden

**Approach:** Opened the file in a text editor and searched (ctrl+f) for the flag format

![image](https://github.com/user-attachments/assets/9b18e5ec-28ac-4c79-ab64-0a054e7504f6)

**Flag:**

```
picoCTF{more_than_m33ts_the_3y3657BaB2C}
```

## Sleuthkit Intro

```
Description
Download the disk image and use mmls on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.
Download disk image
Access checker program: nc saturn.picoctf.net 52439
```

```
root@DhruvsPC:~# mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
root@DhruvsPC:~# nc saturn.picoctf.net 52439
What is the size of the Linux partition in the given disk image?
Length in sectors: 202752
202752
Great work!
picoCTF{mm15_f7w!}
```

**Flag:**

```
picoCTF{mm15_f7w!}
```

## extensions

**Description:**

```
This is a really weird text file TXT? Can you find the flag?
```

**Approach:**

Opened the file in a text editor, it looked like a png. Then I opened the file in a hex editor and confirmed that it has the corect PNG header, saved it as a png and obtained the flag when I opened the png.

![image](https://github.com/user-attachments/assets/bf971cf5-0d43-4ed6-a556-007ff3f55023)

<img width="849" alt="flages" src="https://github.com/user-attachments/assets/61222e7a-e272-4b47-8f97-ac672fd14011">

**Tool Used:** https://hexed.it/

**Flag:**

```
picoCTF{now_you_know_about_extensions}
```

## What Lies Within

**Approach:** I used an online Steganography tool to decode the image and found the flag

![image](https://github.com/user-attachments/assets/94051f07-a34b-4f8c-adbc-d325873188c0)

**Flag:**

```
picoCTF{h1d1ng_1n_th3_b1t5}
```

**Resource used:** https://stylesuxx.github.io/steganography/

## Packets Primer

Download the packet capture file and use packet analysis software to find the flag. - `Wireshark`

![image](https://github.com/user-attachments/assets/afdfb6e1-81ea-45d8-a0fe-11818a8780ab)

**Flag:**

```
picoCTF{p4ck37_5h4rk_ceccaa7f}
```

## Verify

**Approach: Ran the decrypt script for all the files using a simple for loop in the Linux shell**

Command used:

```
for file in files/*; do ./decrypt.sh "$file" ; done
```

```
ctf-player@pico-chall$ ls
checksum.txt  decrypt.sh  files
ctf-player@pico-chall$ ls files
047MJYW7  58VrA22G  AOgyIEGc  FXHBxQjZ  LmicJDs8  QRakKVta  WBbhtpsN  bf4r768r  gkqJibML  orV7qTqZ  uDj1e5QR  xgBUzxwD
0CbGv6a3  5HYKp822  AlGTwKyO  Fv7iksDZ  Lmt5Y0x2  Qi0CXXRR  WBv990nM  bvPuToXm  gmcsCSX3  oy2oXp1t  uJnJfk8o  xjRhyYW5
0E56AVSC  5Hde480w  AmQLyNou  G244hQnd  Lo86CvQ9  Qir73mSK  WEqguSEY  c6c8b911  hBccpGRH  pGGOwBsr  ukl9M0t5  xrUttVxO
0QUxtltc  5K1a6h06  Ar2IDsE2  GDrafQ2W  LxrBh9k1  R0QJ2VKL  WGlw8QMW  cYQJTzGN  hI05TCz1  pOWsomAC  ulFEMOKX  xxr0iXrr
0XKkalUj  5P2RhVCm  BD8hIik3  GHuWjeJ9  M4k3wbII  R9B10IsM  WWTBLhPp  coJvjQ1h  hONfsBJg  pQNOrEf0  umDaEkFr  yAbc0Rj2
0hBYiFqV  5UGLBciS  BtuwzSy0  GUEnrd1t  Ml2ne9bC  RT9fmHCO  WdGGv43K  d3p6iNNZ  hgfq6lwn  pcG2OMtT  uvq4BDCM  yRrCeSQg
0xx1tyUI  5glLfO3M  C8QQ7gyc  Gp1JEl2h  N18is4D1  RiQGT34B  X7yet6uw  dDSS287o  hnC2Necm  pfB7wztg  uw3TvL3P  yi2zkQtL
1VpyYwwh  60CeHYva  CIcPHsac  H7Ixs9CI  NAKaekRz  SFAQKdZD  XF3VmqVm  dDuPGuwH  hsW2u10K  pn2lFoDd  uwZIBYpw  yj7yobL0
25jFiRcF  69891sbg  CJ5U4hxW  HDYiL2qX  NEc5NL3C  SGQH2HKl  XFrufR80  dEVxJ2qG  i2LDbe1K  poTBHw5o  uz0yrxxD  yxVNk723
2B0GV1AB  6ePyVUQ2  CmGCd6Vt  HNRI4jm0  NH1pCwum  SQrS0l9A  XQJcaZgW  dJzWkU1Q  i4XAopa0  pz7WGxJ4  v0LKVD3h  z333mx7V
2SbMywFt  6nFsOudx  D6DGyxjR  HUiJtVz0  NmuLJcjD  SREVuUw3  XqRw2HGU  e7U2gGar  iKj2d6J4  qJIJZA0v  v9TEcwko  zNtZNpTg
2Yc6IWTg  6wnVCfWh  D9zwUVlq  HhPvJ7d7  NqjC5VXz  Sus5gnJ8  XuigwWF7  eHMqnmO6  iMQMDV0F  qiKkh7L2  vC1tHUr2  zSomJYUc
2oGGasVb  7YlIOxWG  DBQbeL0I  Ht3OiHhF  O7knebdG  SzSn7OcI  Y1tTgMUD  eUp5OdvA  jHRn7Fub  qnxF5I1t  vGHNz4al  zUmtlpHw
2xPyec1z  80btcs9b  DRnArSUC  I1gghDYt  O9vttreT  TDjaKG6o  YEjiR5zf  efPoh96A  jvtAQCHw  rAQk2W0n  vL0JYb7n  zjK7vU2n
3HtK7pJ0  80f71Tlc  DSwFiycn  IJX4r4eM  OGiva8vH  TMEQwqGw  YZ0OB1mt  egSaXF3D  lMx8gj9G  rDBnOYi8  vY5qGrrd  zlkIRSOv
3MWxikbL  85k4844c  DgSvTEwj  JB4PaRNY  OHjloRN0  Tb4MR5ML  Ylaf2TY1  enUaRS4w  lURnFs0v  rHtWBcCX  vvJtzkqH
3P2iIh03  86hYDjno  DhGmqcSh  JqYRPdED  OaQl5g3e  TcfR5Cf6  Yn1Qg1dx  eoYlHLVB  lyYImb9U  rK99ez1a  w3o3t3VK
3ZyNMmFE  8SXF7mDb  DpTMOGCI  K4jUiynD  ObjxHPwy  Td52rYaf  Ypof7Dgr  exyTux3t  mMUJICI9  rUmhKhnU  wJD9dCMd
3eJU0bPR  8h1rOlXM  DxlIKqf0  KDp8EJSk  Ofz0iqFX  Texe1REf  ZM8AYtlG  fB2VnieD  mpJ16YYd  sOhwN7cV  wgvRImaG
3qDZ0GiM  9CrGqrOf  EC1I5QwZ  KbONzfRz  Ot4mYM7x  ThXpDtur  ZVhZ6QYU  fJiZ2bMw  nMTwYBYg  sTktzsdS  whevF4V0
3rXzZWry  9VFp8JdD  EXORCadn  Kd0WNtCU  Ous2JVk2  TtY9kI58  ZWNJ0AhH  fKCy1WTf  niXGrsgK  t3MxVbsm  x1wlAOTr
43UId6P7  9YOFaoZl  EfRHiDLP  Keoo2vTu  PJqcmuRt  TxL3f6fM  ZZSXid5R  fPrKO8V5  nr3IXKgz  t3yYcEve  xCDyjqeT
4MQ26j79  9fSkDlcH  Eg5lVJUw  KvvTfLSK  PfmG9EIR  U7SEpsXd  a76e3swH  fQnfnq06  nvtdmSSg  t7jXqCcv  xE1I24IF
4UWHd6Hh  9spBfMu7  ElM3tYhK  LP8coBqU  PvE5OAg4  URYYNGxZ  aUzIEw0T  fnrslV0R  oQzbBXPT  tQQuoksm  xP8hXfNR
4iAgLaET  A0Xjfjyv  FNRT4oFd  LQJNuVhs  Q94hibhx  VR8O9EAS  bE62hGOU  gDXNNquR  onqK4HP3  tjZsxG5L  xQMWIZBH
51fpnVb7  AOAysod6  FWmPesGL  LkGAamWS  QHkh1WHT  W1Fiysnc  bNDt5rfT  gIhaWdn0  opLYnq5q  tzjdKlhj  xVPXvgB2
ctf-player@pico-chall$ for file in files/*; do     ./decrypt.sh "$file" ; done
bad magic number
Error: Failed to decrypt 'files/047MJYW7'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/0CbGv6a3'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/0E56AVSC'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/0QUxtltc'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/0XKkalUj'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/0hBYiFqV'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/0xx1tyUI'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/1VpyYwwh'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/25jFiRcF'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/2B0GV1AB'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/2SbMywFt'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/2Yc6IWTg'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/2oGGasVb'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/2xPyec1z'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/3HtK7pJ0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/3MWxikbL'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/3P2iIh03'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/3ZyNMmFE'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/3eJU0bPR'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/3qDZ0GiM'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/3rXzZWry'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/43UId6P7'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/4MQ26j79'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/4UWHd6Hh'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/4iAgLaET'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/51fpnVb7'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/58VrA22G'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/5HYKp822'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/5Hde480w'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/5K1a6h06'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/5P2RhVCm'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/5UGLBciS'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/5glLfO3M'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/60CeHYva'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/69891sbg'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/6ePyVUQ2'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/6nFsOudx'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/6wnVCfWh'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/7YlIOxWG'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/80btcs9b'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/80f71Tlc'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/85k4844c'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/86hYDjno'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/8SXF7mDb'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/8h1rOlXM'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/9CrGqrOf'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/9VFp8JdD'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/9YOFaoZl'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/9fSkDlcH'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/9spBfMu7'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/A0Xjfjyv'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/AOAysod6'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/AOgyIEGc'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/AlGTwKyO'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/AmQLyNou'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Ar2IDsE2'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/BD8hIik3'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/BtuwzSy0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/C8QQ7gyc'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/CIcPHsac'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/CJ5U4hxW'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/CmGCd6Vt'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/D6DGyxjR'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/D9zwUVlq'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/DBQbeL0I'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/DRnArSUC'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/DSwFiycn'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/DgSvTEwj'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/DhGmqcSh'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/DpTMOGCI'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/DxlIKqf0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/EC1I5QwZ'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/EXORCadn'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/EfRHiDLP'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Eg5lVJUw'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ElM3tYhK'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/FNRT4oFd'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/FWmPesGL'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/FXHBxQjZ'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Fv7iksDZ'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/G244hQnd'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/GDrafQ2W'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/GHuWjeJ9'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/GUEnrd1t'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Gp1JEl2h'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/H7Ixs9CI'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/HDYiL2qX'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/HNRI4jm0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/HUiJtVz0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/HhPvJ7d7'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Ht3OiHhF'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/I1gghDYt'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/IJX4r4eM'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/JB4PaRNY'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/JqYRPdED'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/K4jUiynD'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/KDp8EJSk'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/KbONzfRz'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Kd0WNtCU'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Keoo2vTu'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/KvvTfLSK'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/LP8coBqU'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/LQJNuVhs'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/LkGAamWS'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/LmicJDs8'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Lmt5Y0x2'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Lo86CvQ9'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/LxrBh9k1'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/M4k3wbII'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Ml2ne9bC'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/N18is4D1'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/NAKaekRz'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/NEc5NL3C'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/NH1pCwum'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/NmuLJcjD'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/NqjC5VXz'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/O7knebdG'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/O9vttreT'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/OGiva8vH'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/OHjloRN0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/OaQl5g3e'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ObjxHPwy'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Ofz0iqFX'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Ot4mYM7x'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Ous2JVk2'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/PJqcmuRt'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/PfmG9EIR'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/PvE5OAg4'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Q94hibhx'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/QHkh1WHT'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/QRakKVta'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Qi0CXXRR'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Qir73mSK'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/R0QJ2VKL'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/R9B10IsM'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/RT9fmHCO'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/RiQGT34B'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/SFAQKdZD'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/SGQH2HKl'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/SQrS0l9A'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/SREVuUw3'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Sus5gnJ8'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/SzSn7OcI'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/TDjaKG6o'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/TMEQwqGw'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Tb4MR5ML'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/TcfR5Cf6'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Td52rYaf'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Texe1REf'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ThXpDtur'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/TtY9kI58'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/TxL3f6fM'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/U7SEpsXd'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/URYYNGxZ'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/VR8O9EAS'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/W1Fiysnc'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/WBbhtpsN'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/WBv990nM'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/WEqguSEY'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/WGlw8QMW'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/WWTBLhPp'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/WdGGv43K'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/X7yet6uw'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/XF3VmqVm'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/XFrufR80'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/XQJcaZgW'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/XqRw2HGU'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/XuigwWF7'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Y1tTgMUD'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/YEjiR5zf'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/YZ0OB1mt'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Ylaf2TY1'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Yn1Qg1dx'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/Ypof7Dgr'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ZM8AYtlG'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ZVhZ6QYU'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ZWNJ0AhH'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ZZSXid5R'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/a76e3swH'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/aUzIEw0T'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/bE62hGOU'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/bNDt5rfT'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/bf4r768r'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/bvPuToXm'. This flag is fake! Keep looking!
picoCTF{trust_but_verify_c6c8b911}
bad magic number
Error: Failed to decrypt 'files/cYQJTzGN'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/coJvjQ1h'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/d3p6iNNZ'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/dDSS287o'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/dDuPGuwH'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/dEVxJ2qG'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/dJzWkU1Q'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/e7U2gGar'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/eHMqnmO6'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/eUp5OdvA'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/efPoh96A'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/egSaXF3D'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/enUaRS4w'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/eoYlHLVB'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/exyTux3t'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/fB2VnieD'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/fJiZ2bMw'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/fKCy1WTf'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/fPrKO8V5'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/fQnfnq06'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/fnrslV0R'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/gDXNNquR'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/gIhaWdn0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/gkqJibML'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/gmcsCSX3'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/hBccpGRH'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/hI05TCz1'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/hONfsBJg'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/hgfq6lwn'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/hnC2Necm'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/hsW2u10K'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/i2LDbe1K'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/i4XAopa0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/iKj2d6J4'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/iMQMDV0F'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/jHRn7Fub'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/jvtAQCHw'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/lMx8gj9G'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/lURnFs0v'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/lyYImb9U'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/mMUJICI9'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/mpJ16YYd'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/nMTwYBYg'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/niXGrsgK'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/nr3IXKgz'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/nvtdmSSg'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/oQzbBXPT'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/onqK4HP3'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/opLYnq5q'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/orV7qTqZ'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/oy2oXp1t'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/pGGOwBsr'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/pOWsomAC'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/pQNOrEf0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/pcG2OMtT'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/pfB7wztg'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/pn2lFoDd'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/poTBHw5o'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/pz7WGxJ4'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/qJIJZA0v'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/qiKkh7L2'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/qnxF5I1t'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/rAQk2W0n'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/rDBnOYi8'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/rHtWBcCX'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/rK99ez1a'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/rUmhKhnU'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/sOhwN7cV'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/sTktzsdS'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/t3MxVbsm'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/t3yYcEve'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/t7jXqCcv'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/tQQuoksm'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/tjZsxG5L'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/tzjdKlhj'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/uDj1e5QR'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/uJnJfk8o'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ukl9M0t5'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/ulFEMOKX'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/umDaEkFr'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/uvq4BDCM'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/uw3TvL3P'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/uwZIBYpw'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/uz0yrxxD'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/v0LKVD3h'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/v9TEcwko'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/vC1tHUr2'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/vGHNz4al'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/vL0JYb7n'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/vY5qGrrd'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/vvJtzkqH'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/w3o3t3VK'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/wJD9dCMd'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/wgvRImaG'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/whevF4V0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/x1wlAOTr'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xCDyjqeT'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xE1I24IF'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xP8hXfNR'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xQMWIZBH'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xVPXvgB2'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xgBUzxwD'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xjRhyYW5'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xrUttVxO'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/xxr0iXrr'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/yAbc0Rj2'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/yRrCeSQg'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/yi2zkQtL'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/yj7yobL0'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/yxVNk723'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/z333mx7V'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/zNtZNpTg'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/zSomJYUc'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/zUmtlpHw'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/zjK7vU2n'. This flag is fake! Keep looking!
bad magic number
Error: Failed to decrypt 'files/zlkIRSOv'. This flag is fake! Keep looking!
ctf-player@pico-chall$ Connection to rhea.picoctf.net closed by remote host.
Connection to rhea.picoctf.net closed.
```

**Flag:**

```
picoCTF{trust_but_verify_c6c8b911}
```

**Knowledge Gained:**

Usage of loops in the Linux shell
