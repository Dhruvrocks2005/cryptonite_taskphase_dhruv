# General Skills - Extra Challenges

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

## ASCII Numbers

![image](https://github.com/user-attachments/assets/b888870d-5012-4476-b9b0-91f725e63c6b)

**Flag:**

```
picoCTF{45c11_n0_qu35710n5_1ll_t311_y3_n0_l135_445d4180}
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
