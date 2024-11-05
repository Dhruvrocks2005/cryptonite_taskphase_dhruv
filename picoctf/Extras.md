# General Skills

## Binary Search

**Approach: Used Binary Search Algorithm to guess the number**

```
root@DhruvsPC:~# ssh -p 62073 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:62073 ([18.217.83.136]:62073)' can't be established.
ED25519 key fingerprint is SHA256:M8hXanE8l/Yzfs8iuxNsuFL4vCzCKEIlM/3hpO13tfQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:62073' (ED25519) to the list of known hosts.
ctf-player@atlas.picoctf.net's password:
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Higher! Try again.
Enter your guess: 750
Lower! Try again.
Enter your guess: 625
Lower! Try again.
Enter your guess: 562
Lower! Try again.
Enter your guess: 531
Lower! Try again.
Enter your guess: 515
Lower! Try again.
Enter your guess: 507
Higher! Try again.
Enter your guess: 511
Higher! Try again.
Enter your guess: 513
Lower! Try again.
Enter your guess: 512
Congratulations! You guessed the correct number: 512
Here's your flag: picoCTF{g00d_gu355_3af33d18}
Connection to atlas.picoctf.net closed.
```

**Flag:**

```
picoCTF{g00d_gu355_3af33d18}
```

## Time Machine

```
Description
What was I last working on? I remember writing a note to help me remember...
```

**Approach: Found the flag in the `challenge\drop-in\.git\COMMIT_EDITMSG` , `challenge\drop-in\.git\logs\HEAD` and `challenge\drop-in\.git\logs\refs\heads\master` files**


![image](https://github.com/user-attachments/assets/20e32bf0-3c23-485d-9ee6-b386c6be0b41)

![image](https://github.com/user-attachments/assets/c56f4efc-24ff-46d6-b0a9-c5cf18ebdcc5)

**Flag:**

```
picoCTF{t1m3m@ch1n3_186cd7d7}
```

# Binary Exploitation

## heap 0

**Approach: Exploit heap overflow vulnerability**

We need to modify `safe_var` to a value other than `"bico"` so that the `check_win()` function will print the flag.

Since both `input_data` and `safe_var` are allocated close to each other on the heap, if we overflow `input_data`, it will spill over into `safe_var`, allowing us to modify its contents.

```
Welcome to heap0!
I put my data on the heap so it should be safe from any tampering.
Since my data isn't on the stack I'll even let you write whatever info you want to the heap, I already took care of using malloc for you.

Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data
+-------------+----------------+
[*]   0x62ca8e36f2b0  ->   pico
+-------------+----------------+
[*]   0x62ca8e36f2d0  ->   bico
+-------------+----------------+

1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 2
Data for buffer: 1234567890123456789012345678901234567890

1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 1
Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data
+-------------+----------------+
[*]   0x62ca8e36f2b0  ->   1234567890123456789012345678901234567890
+-------------+----------------+
[*]   0x62ca8e36f2d0  ->   34567890
+-------------+----------------+

1. Print Heap:          (print the current state of the heap)
2. Write to buffer:     (write to your own personal block of data on the heap)
3. Print safe_var:      (I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:          (Try to print the flag, good luck)
5. Exit

Enter your choice: 4

YOU WIN
picoCTF{my_first_heap_overflow_4fa6dd49}

```

**Flag:**

```
picoCTF{my_first_heap_overflow_4fa6dd49}
```

# Forensics

## Scan Surprise

![flag](https://github.com/user-attachments/assets/1077a5c8-9b8b-434f-bf16-955f38484720)

**Approach: Used Google Lens to scan the qr and found the flag.**

![IMG_20241106_000018](https://github.com/user-attachments/assets/3b6fd10a-204b-4afe-8445-d86d01f7cf1a)

**Flag:**

```
picoCTF{p33k_@_b00_a81f0a35}
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

# Web Exploitation

## WebDecode

**Approach: Inspected the page and then decoded the encoded flag hidden there**

![image](https://github.com/user-attachments/assets/6552e059-c314-46e4-a3ab-25f6acadb724)

**Encoded Flag:**

```
cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMDJjZGNiNTl9
```

The encoded string is in Base64 format. Decoding it reveals the flag.

![image](https://github.com/user-attachments/assets/ce77c7f2-98ee-4eaf-8ec1-1c9ee08f6504)

**Flag:**

```
picoCTF{web_succ3ssfully_d3c0ded_02cdcb59}
```

## Unminify

**Approach: Found the flag upon inspecting the page**

![image](https://github.com/user-attachments/assets/36e85b58-e2a6-4930-bd50-43304840dc57)

**Flag:**

```
picoCTF{pr3tty_c0d3_b99eb82e}
```
