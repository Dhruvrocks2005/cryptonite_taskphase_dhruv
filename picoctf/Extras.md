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

## Obedient Cat

**Approach: Just open the downloaded file in a text editor or cat it in linux**

```
root@DhruvsPC:~# cat flag
picoCTF{s4n1ty_v3r1f13d_1a94e0f9}
```

**Flag:**

```
picoCTF{s4n1ty_v3r1f13d_1a94e0f9}
```

## Super SSH

![image](https://github.com/user-attachments/assets/e50b37f5-e5ed-45ee-9a99-bb7015c68644)

```
root@DhruvsPC:~# ssh -p 64948 ctf-player@titan.picoctf.net
The authenticity of host '[titan.picoctf.net]:64948 ([3.139.174.234]:64948)' can't be established.
ED25519 key fingerprint is SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5kudRP9PIKT7XQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[titan.picoctf.net]:64948' (ED25519) to the list of known hosts.
ctf-player@titan.picoctf.net's password:
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_45a48857}
Connection to titan.picoctf.net closed.
```

**Flag:**

```
picoCTF{s3cur3_c0nn3ct10n_45a48857}
```

## what's a net cat?

```
Description
Using netcat (nc) is going to be pretty important. Can you connect to jupiter.challenges.picoctf.org at port 25103 to get the flag?
```
- `nc` is the command for `netcat`, a tool that can read and write data across network connections.
- `jupiter.challenges.picoctf.org` is the server’s domain.
- `25103` is the port to connect to on that server.
```
root@DhruvsPC:~# nc jupiter.challenges.picoctf.org 25103
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_d0c64587}
```

**Flag:**

```
picoCTF{nEtCat_Mast3ry_d0c64587}
```

**Knowledge Gained:**

`nc` command

Recources: https://linux.die.net/man/1/nc

## Nice netcat...

```
root@DhruvsPC:~# nc mercury.picoctf.net 35652
112
105
99
111
67
84
70
123
103
48
48
100
95
107
49
116
116
121
33
95
110
49
99
51
95
107
49
116
116
121
33
95
57
98
51
98
55
51
57
50
125
10
```
![image](https://github.com/user-attachments/assets/947bce2e-7741-4ce1-93e0-305748e2ed1f)

**Flag:**

```
picoCTF{g00d_k1tty!_n1c3_k1tty!_9b3b7392}
```

## Glitch Cat

```
root@DhruvsPC:~# nc saturn.picoctf.net 58943
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
```

Each chr(0x..) converts a hexadecimal ASCII code into a character.


![image](https://github.com/user-attachments/assets/3510f65b-8a15-4136-bc74-e6158ed286cd)

**Flag:**

```
picoCTF{gl17ch_m3_n07_bda68f75}
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

## Warmed Up

What is 0x3D (base 16) in decimal (base 10)?

![image](https://github.com/user-attachments/assets/8e9fa886-907c-43d9-ae2e-01a0a7922902)

**Flag:**

```
picoCTF{61}
```

## 2Warm

Can you convert the number 42 (base 10) to binary (base 2)?

![image](https://github.com/user-attachments/assets/28b2ea92-4041-44f7-88a2-2dd89a1e56cc)

**Flag:**

```
picoCTF{101010}
```

## Bases

What does this bDNhcm5fdGgzX3IwcDM1 mean? I think it has something to do with bases.

![image](https://github.com/user-attachments/assets/c6f9f638-dab1-4a36-94d3-d42affdb0f8d)

**Flag:**

```
picoCTF{l3arn_th3_r0p35}
```

## Wave a flag

Approach: Just executed the file and followed the instructions

Gave myself (user/owner/root) permission to execute the file using chmod command leanrt in task phase 1 

```
root@DhruvsPC:~# ./warm
-bash: ./warm: Permission denied
root@DhruvsPC:~# ls -l warm
-rw-r--r-- 1 root root 10936 Nov  6 03:50 warm
root@DhruvsPC:~# chmod u+x warm
root@DhruvsPC:~# ./warm
Hello user! Pass me a -h to learn what I can do!
root@DhruvsPC:~# -h
-h: command not found
root@DhruvsPC:~# ./warm -h
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_d6969390}
```

**Flag:**

```
picoCTF{b1scu1ts_4nd_gr4vy_d6969390}
```

## Tab, Tab, Attack

Approach: Just followed the instructions and found the flag

```
root@DhruvsPC:~# cd Addadshashanammu/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/
root@DhruvsPC:~/Addadshashanammu/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku# ls
fang-of-haynekhtnamet  fang-of-haynekhtnamet:Zone.Identifier
root@DhruvsPC:~/Addadshashanammu/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku# ./fang-of-haynekhtnamet
-bash: ./fang-of-haynekhtnamet: Permission denied
root@DhruvsPC:~/Addadshashanammu/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku# ls -l fang-of-haynekhtnamet
-rw-r--r-- 1 root root 8320 Nov  6 03:56 fang-of-haynekhtnamet
root@DhruvsPC:~/Addadshashanammu/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku# chmod u+x fang-of-haynekhtnamet
root@DhruvsPC:~/Addadshashanammu/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku# ./fang-of-haynekhtnamet
*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_d32e018c}
```

**Flag:**

```
picoCTF{l3v3l_up!_t4k3_4_r35t!_d32e018c}
```

**Knowledge Gained:** Using tabcomplete in the Terminal 

## strings it

In this challenge, we were given a binary file that contains the flag. We needed to extract this flag by analyzing the strings in the file.

**Approach:**

I ran the `strings` command on the given file, redirecting the output to a file named `olaola`. This step captured all readable strings in the file.
Finally, I used `grep` to search for the flag format, `picoCTF`, within `olaola`.

```
root@DhruvsPC:~# touch olaola
root@DhruvsPC:~# strings strings > olaola
root@DhruvsPC:~# grep 'picoCTF' olaola
picoCTF{5tRIng5_1T_7f766a23}
```

**Flag:**

```
picoCTF{5tRIng5_1T_7f766a23}
```

**Knowledge Gained:**

`strings` command extracts readable ASCII characters from binary files, which can reveal hidden information like flags.

## First Grep

We can grep the flag from the file using the default flag format, as intended, OR we could just use ctrl+f in the file (opened in a text editor)'

```
root@DhruvsPC:~# grep 'picoCTF' file
picoCTF{grep_is_good_to_find_things_5af9d829}
```

![image](https://github.com/user-attachments/assets/69c98195-a398-4780-9f6c-cabca261557c)

**Flag:**

```
picoCTF{grep_is_good_to_find_things_5af9d829}
```

## Python Wrangling

```
Python scripts are invoked kind of like programs in the Terminal... 
Can you run this Python script (ende.py) using this password (6008014f6008014f6008014f6008014f) to get the flag (flag.txt.en) ?
```

```
root@DhruvsPC:~# python3 ende.py -d flag.txt.en
Please enter the password:6008014f6008014f6008014f6008014f
picoCTF{4p0110_1n_7h3_h0us3_6008014f}
```

**Flag:**

```
picoCTF{4p0110_1n_7h3_h0us3_6008014f}
```

**Knowledge Gained:** Learnt how to run python scripts on the terminal

## PW Crack 1

![image](https://github.com/user-attachments/assets/10572336-24b1-4a66-9c9f-2a5509919df8)

From the given code, required password is `8713`

```
root@DhruvsPC:~# python3 level1.py
Please enter correct password for flag: 8713
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_1b2fd683}
```

**Flag:**

```
picoCTF{545h_r1ng1ng_1b2fd683}
```

## PW Crack 2

![image](https://github.com/user-attachments/assets/629798a3-f7bb-4f3b-8455-8a48aefe19fb)

From the given code, required password is `chr(0x34) + chr(0x65) + chr(0x63) + chr(0x39)` which is `4ec9` (converting each hexadecimal value into its corresponding ASCII character)

```
root@DhruvsPC:~# python3 level2.py
Please enter correct password for flag: 4ec9
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_9701e681}
```

**Flag:**

```
picoCTF{tr45h_51ng1ng_9701e681}
```

## PW Crack 3

```
Description
Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag and the hash in the same directory too.
There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.
```

![image](https://github.com/user-attachments/assets/b6d69c17-11aa-4414-b1e1-d9b31ab15af3)

```
root@DhruvsPC:~# python3 level3.py
Please enter correct password for flag: 8799
That password is incorrect
root@DhruvsPC:~# python3 level3.py
Please enter correct password for flag: d3ab
That password is incorrect
root@DhruvsPC:~# python3 level3.py
Please enter correct password for flag: 1ea2
That password is incorrect
root@DhruvsPC:~# python3 level3.py
Please enter correct password for flag: acaf
That password is incorrect
root@DhruvsPC:~# python3 level3.py
Please enter correct password for flag: 2295
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_6f98a49f}
```

**Flag:**

```
picoCTF{m45h_fl1ng1ng_6f98a49f}
```

## PW Crack 4

**Description:**

```
Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag and the hash in the same directory too.
There are 100 potential passwords with only 1 being correct. You can find these by examining the password checker script.
```

**cracker.py:**

```
import hashlib

# Provided encrypted flag and hash values
flag_enc = open('level4.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level4.hash.bin', 'rb').read()

# Function to hash passwords
def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

# XOR decryption function
def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])

# List of potential passwords
pos_pw_list = ["158f", "1655", "d21e", "4966", "ed69", "1010", "dded", "844c", "40ab", "a948", "156c", "ab7f", "4a5f", 
               "e38c", "ba12", "f7fd", "d780", "4f4d", "5ba1", "96c5", "55b9", "8a67", "d32b", "aa7a", "514b", "e4e1", 
               "1230", "cd19", "d6dd", "b01f", "fd2f", "7587", "86c2", "d7b8", "55a2", "b77c", "7ffe", "4420", "e0ee", 
               "d8fb", "d748", "b0fe", "2a37", "a638", "52db", "51b7", "5526", "40ed", "5356", "6ad4", "2ddd", "177d", 
               "84ae", "cf88", "97a3", "17ad", "7124", "eff2", "e373", "c974", "7689", "b8b2", "e899", "d042", "47d9", 
               "cca9", "ab2a", "de77", "4654", "9ecb", "ab6e", "bb8e", "b76b", "d661", "63f8", "7095", "567e", "b837", 
               "2b80", "ad4f", "c514", "ffa4", "fc37", "7254", "b48b", "d38b", "a02b", "ec6c", "eacc", "8b70", "b03e", 
               "1b36", "81ff", "77e4", "dbe6", "59d9", "fd6a", "5653", "8b95", "d0e5"]

# Find the correct password
for password in pos_pw_list:
    if hash_pw(password) == correct_pw_hash:
        print(f"Correct password found: {password}")
        
        # Decrypt the flag
        decrypted_flag = str_xor(flag_enc.decode(), password)
        print("Decrypted Flag:", decrypted_flag)
        break

```

**Running the program:**

```
root@DhruvsPC:~# touch cracker.py
root@DhruvsPC:~# python3 cracker.py
Correct password found: 8b95
Decrypted Flag: picoCTF{fl45h_5pr1ng1ng_cf341ff1}
```

**Flag:**

```
picoCTF{fl45h_5pr1ng1ng_cf341ff1}
```

## PW Crack 5

**Description:**

```
Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag and the hash in the same directory too. Here's a dictionary with all possible passwords based on the password conventions we've seen so far.
```

**checker.py:**

```
import hashlib

# Read the encrypted flag and correct password hash
flag_enc = open('level5.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level5.hash.bin', 'rb').read()

# Function to hash passwords
def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

# XOR decryption function
def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c, new_key_c) in zip(secret, new_key)])

# Load the dictionary of possible passwords
with open('dictionary.txt', 'r') as f:
    pos_pw_list = f.read().splitlines()

# Iterate through each password in the dictionary
for password in pos_pw_list:
    if hash_pw(password) == correct_pw_hash:
        print(f"Correct password found: {password}")
        
        # Decrypt the flag
        decrypted_flag = str_xor(flag_enc.decode(), password)
        print("Decrypted Flag:", decrypted_flag)
        break
```

**Running the program:**

```
root@DhruvsPC:~# touch checker.py
root@DhruvsPC:~# python3 checker.py
Correct password found: eee0
Decrypted Flag: picoCTF{h45h_sl1ng1ng_fffcda23}
```

**Flag:**

```
picoCTF{h45h_sl1ng1ng_fffcda23}
```

## Big Zip

**Knowledge gained:** 
`grep` can be instructed to search through all files in a directory and its subdirectories using the `-r` (recursive) option

```
root@DhruvsPC:~# grep 'picoCTF' big-zip-files
grep: big-zip-files: Is a directory
root@DhruvsPC:~# grep -r 'picoCTF' big-zip-files
big-zip-files/big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```

**Flag:**

```
 picoCTF{gr3p_15_m4g1c_ef8790dc}
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

## Enhance!

**Approach:** Found the flag when I opened the file in a text editor

![image](https://github.com/user-attachments/assets/0ea707cf-86b6-4d1a-9a47-92ad0ce4b044)

![image](https://github.com/user-attachments/assets/6d0191f9-aa21-4a4f-9c71-cb460e4f320b)

**Flag:**

```
picoCTF{3nh4nc3d_aab729dd}
```

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

## Insp3ct0r

**Approach: I just inspected the page and found the flag divided into 3 parts, hidden in the `HTML`, `CSS`, `JS (JavaScript)`
source codes of the webpage**

![image](https://github.com/user-attachments/assets/e2440838-f980-482e-a90e-994fc10d38ae)

`HTML`, `CSS`, `JS (JavaScript)`

![image](https://github.com/user-attachments/assets/ccbc6d99-346f-4ff9-aae4-19bfd4c00bf3)

```
Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 
```

![image](https://github.com/user-attachments/assets/1464dfa2-9f3b-42e7-98f3-d6117022907a)

```
You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t
```

![image](https://github.com/user-attachments/assets/4c93905e-0f3c-4b18-b3a2-bedd17e1ce62)

```
Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?832b0699}
```

**Flag:**

```
picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?832b0699}
```

## where are the robots

**Approach:** I knew about robots.txt from OASIS CTF so this was very straightforward

**website link:** https://jupiter.challenges.picoctf.org/problem/60915/

![image](https://github.com/user-attachments/assets/fed1aed0-115e-45b0-92bc-a3de892b4025)

<br>

**website link:** https://jupiter.challenges.picoctf.org/problem/60915/robots.txt

![image](https://github.com/user-attachments/assets/67a163fa-5941-43b0-acc9-554f6a7b0264)

<br>

**website link:** https://jupiter.challenges.picoctf.org/problem/60915/8028f.html

![image](https://github.com/user-attachments/assets/1bef6dbe-f027-406a-ab38-a16df7b46a2c)

<br>

**Flag:**

```
picoCTF{ca1cu1at1ng_Mach1n3s_8028f}
```

# Cryptography

## interencdec

```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==
```

Given string was encoded in base64.

![image](https://github.com/user-attachments/assets/8cd3a341-d77e-4ad0-8836-7c57ae9c57b9)

```
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ=='
```

After decoding it, the result also seemed to be encoded in base64.

![image](https://github.com/user-attachments/assets/c98eedf1-fecd-4443-8e70-7ade9a2cc8bd)

```
wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}
```

After decoding it, the result seemed to be encoded in caesar cypher.

![image](https://github.com/user-attachments/assets/baf4d070-c728-48b5-92d2-ba60b8904ac6)

After decoding it, I found the flag.

**Flag:**

```
picoCTF{caesar_d3cr9pt3d_78250afc}
```

Tool used: https://cryptii.com/

## Mod 26

ROT13 is a simple substitution cipher that shifts each letter 13 positions in the alphabet. Applying ROT13 again on the encoded text will return the original text.

**Encoded text:**

```
cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_nSkgmDJE}
```

![image](https://github.com/user-attachments/assets/9b4d23a6-23c4-4fdb-8468-ec08090fb06d)

**Decoded text:**

```
picoCTF{next_time_I'll_try_2_rounds_of_rot13_aFxtzQWR}
```

**Flag:**

```
picoCTF{next_time_I'll_try_2_rounds_of_rot13_aFxtzQWR}
```

## substitution0

Tool used: https://planetcalc.com/8047/

![image](https://github.com/user-attachments/assets/dee7d8c9-de6e-47b3-97ae-65798671b63b)

**Flag:**

```
picoCTF{5UB5717U710N_3V0LU710N_357BF9FF}
```

## substitution1

Tool used: https://planetcalc.com/8047/

![image](https://github.com/user-attachments/assets/505e2687-15d6-4ad2-8d0d-8c77e8466707)

![image](https://github.com/user-attachments/assets/9ca576c8-f25d-4eb5-ae75-e4d5a5db9799)

![image](https://github.com/user-attachments/assets/a6cfee76-a3f6-4e5a-bb6d-2812f2265b64)

![image](https://github.com/user-attachments/assets/ab6c65a4-b5a0-42a8-848f-c7cce135fb3a)

There were no instances of `J`, `Z`, `X` or `Q` in the decrypted paragraph so the flag could be calculated with permutation and combination but even that was not required since it was obvious which character('Q') would be used as the flag is in leetspeak.

**Flag:**

```
picoCTF{FR3QU3NCY_4774CK5_4R3_C001_7AA384BC}
```

## substitution2

Tool used: https://planetcalc.com/8047/

![image](https://github.com/user-attachments/assets/74a92857-baaf-46e9-8fdc-a4fbe81a4e1f)

**Flag:**

```
picoCTF{N6R4M_4N41Y515_15_73D10U5_8E1BF808}
```

# Reverse Engineering

## vault-door-training

**Approach:** The flag is given in the program's source code

```
import java.util.*;

class VaultDoorTraining {
    public static void main(String args[]) {
        VaultDoorTraining vaultDoor = new VaultDoorTraining();
        Scanner scanner = new Scanner(System.in); 
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
   }

    // The password is below. Is it safe to put the password in the source code?
    // What if somebody stole our source code? Then they would know what our
    // password is. Hmm... I will think of some ways to improve the security
    // on the other doors.
    //
    // -Minion #9567
    public boolean checkPassword(String password) {
        return password.equals("w4rm1ng_Up_w1tH_jAv4_be8d9806f18");
    }
}
```

**Flag:**

```
picoCTF{w4rm1ng_Up_w1tH_jAv4_be8d9806f18}
```
## vault-door-1

**Approach:** The flag is given in the program's source code

Source Code:

```
import java.util.*;

class VaultDoor1 {
    public static void main(String args[]) {
        VaultDoor1 vaultDoor = new VaultDoor1();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
	String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
    }

    // I came up with a more secure way to check the password without putting
    // the password itself in the source code. I think this is going to be
    // UNHACKABLE!! I hope Dr. Evil agrees...
    //
    // -Minion #8728
    public boolean checkPassword(String password) {
        return password.length() == 32 &&
               password.charAt(0)  == 'd' &&
               password.charAt(29) == 'a' &&
               password.charAt(4)  == 'r' &&
               password.charAt(2)  == '5' &&
               password.charAt(23) == 'r' &&
               password.charAt(3)  == 'c' &&
               password.charAt(17) == '4' &&
               password.charAt(1)  == '3' &&
               password.charAt(7)  == 'b' &&
               password.charAt(10) == '_' &&
               password.charAt(5)  == '4' &&
               password.charAt(9)  == '3' &&
               password.charAt(11) == 't' &&
               password.charAt(15) == 'c' &&
               password.charAt(8)  == 'l' &&
               password.charAt(12) == 'H' &&
               password.charAt(20) == 'c' &&
               password.charAt(14) == '_' &&
               password.charAt(6)  == 'm' &&
               password.charAt(24) == '5' &&
               password.charAt(18) == 'r' &&
               password.charAt(13) == '3' &&
               password.charAt(19) == '4' &&
               password.charAt(21) == 'T' &&
               password.charAt(16) == 'H' &&
               password.charAt(27) == '6' &&
               password.charAt(30) == 'f' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == 'd' &&
               password.charAt(26) == 'f' &&
               password.charAt(31) == '4';
    }
}

```

Upon unscrambling it:

```
password.charAt(0)  == 'd'
password.charAt(1)  == '3'
password.charAt(2)  == '5'
password.charAt(3)  == 'c'
password.charAt(4)  == 'r'
password.charAt(5)  == '4'
password.charAt(6)  == 'm'
password.charAt(7)  == 'b'
password.charAt(8)  == 'l'
password.charAt(9)  == '3'
password.charAt(10) == '_'
password.charAt(11) == 't'
password.charAt(12) == 'H'
password.charAt(13) == '3'
password.charAt(14) == '_'
password.charAt(15) == 'c'
password.charAt(16) == 'H'
password.charAt(17) == '4'
password.charAt(18) == 'r'
password.charAt(19) == '4'
password.charAt(20) == 'c'
password.charAt(21) == 'T'
password.charAt(22) == '3'
password.charAt(23) == 'r'
password.charAt(24) == '5'
password.charAt(25) == '_'
password.charAt(26) == 'f'
password.charAt(27) == '6'
password.charAt(28) == 'd'
password.charAt(29) == 'a'
password.charAt(30) == 'f'
password.charAt(31) == '4'
```

**Flag:**

```
picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_f6daf4}
```

## keygenme-py

The flag is `picoCTF{1n_7h3_|<3y_of_xxxxxxxx}` where `xxxxxxxx` is the dynamic part that changes based on the username `SCHOFIELD`.

The dynamic part of the flag is derived from the username SCHOFIELD by hashing it with SHA-256 and extracting specific characters from the hash.

The code specifically grabs the following characters from the SHA-256 hash: hash[4], hash[5], hash[3, ]hash[6], hash[2], hash[7], hash[1], hash[8].

Calculating the dynamic part of the flag:

![image](https://github.com/user-attachments/assets/b117489f-c1ab-4e59-80c9-026d8b3ed624)

**Flag:**

```
picoCTF{1n_7h3_|<3y_of_e584b363}
```

## Safe Opener

Program:
```
import java.io.*;
import java.util.*;  
public class SafeOpener {
    public static void main(String args[]) throws IOException {
        BufferedReader keyboard = new BufferedReader(new InputStreamReader(System.in));
        Base64.Encoder encoder = Base64.getEncoder();
        String encodedkey = "";
        String key = "";
        int i = 0;
        boolean isOpen;
        

        while (i < 3) {
            System.out.print("Enter password for the safe: ");
            key = keyboard.readLine();

            encodedkey = encoder.encodeToString(key.getBytes());
            System.out.println(encodedkey);
              
            isOpen = openSafe(encodedkey);
            if (!isOpen) {
                System.out.println("You have  " + (2 - i) + " attempt(s) left");
                i++;
                continue;
            }
            break;
        }
    }
    
    public static boolean openSafe(String password) {
        String encodedkey = "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz";
        
        if (password.equals(encodedkey)) {
            System.out.println("Sesame open");
            return true;
        }
        else {
            System.out.println("Password is incorrect\n");
            return false;
        }
    }
}
```

According to the program, the encoded key is `cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz`, which is encoded in Base64.

![image](https://github.com/user-attachments/assets/d1bcd48c-1cda-4b84-824e-f7d8fb556910)

**Flag:**

```
picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}
```

## Safe Opener 2

I found the flag when I opened the file with a text editor.

![image](https://github.com/user-attachments/assets/30886d31-17de-4e27-9ee8-92d6b09b1869)

**Flag:**

```
picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_198203f7}
```
