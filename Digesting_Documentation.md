# Digesting Documentation

Fourth Module

## Learning From Documentation

   The documentation indicated that the program requires the argument `--giveflag` to function correctly.
<br>
   I ran the command with the specified argument:
   ```
   /challenge/challenge --giveflag
   ```
   This resulted in the following output:
   ```
   pwn.college{4sUkRDikielJnD5PRNEj3XwPUqn.dRjM5QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/2f560ddb-9a91-4189-b4e0-354b371d5eb9)


## Learning Complex Usage

   The documentation specified that the program requires the `--printfile` argument followed by the path to the file you wish to print. In this case, we needed to access the flag.
<br>
   I ran the following command to retrieve the flag:
   ```
   /challenge/challenge --printfile /flag
   ```
   The output was:
   ```
   pwn.college{05x6Vx2muf44-tOxUO-8oSW_1ez.dVjM5QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/4ad2b3d8-fd84-4b6e-9589-75107858eab0)

## Reading Manuals

   To discover the secret option for the `challenge` command, I ran:
   ```
   man challenge
   ```
   This displayed the manual for the `challenge` command, which included various options.
<br>
   The manual specified the following relevant option:
   ```
   --osdran NUM
       print the flag if NUM is 436
   ```

   I used the identified option to print the flag:
   ```
   /challenge/challenge --osdran 436
   ```
   The output was:
   ```
   pwn.college{oI_4RNFs3UOdrX6-GaEn6L_vzmM.dRTM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/fe6ad340-c90c-4cb3-b104-864f0e5b4e40)


## Searching Manuals

   To find the relevant option for the `challenge` command, I executed:
   ```
   man challenge
   ```

   I used the search feature in the `man` page:
   - To search for keywords related to flags, I pressed `/` followed by `flag`.
   - This allowed me to quickly locate the specific option that prints the flag.
     
<br>

   After finding the relevant option, I ran:
   ```
   /challenge/challenge --gzd
   ```
   The output was:
   ```
   pwn.college{ky0-8Qd7qArZWazwy-1X73fSqvB.dVTM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/27310310-30bd-49af-bbf2-b727e79e77ff)


## Searching For Manuals

In this challenge, we were tasked with finding the hidden man page for the `/challenge/challenge` command, which had a randomized name. The objective was to utilize the `man` command effectively to locate the man page that provided the necessary arguments to obtain the flag.

<br>

   To understand how to search for man pages, I executed:
   ```
   man man
   ```
   This provided detailed information about the usage of the `man` command.

<br>

I used the `-k` option with the `man` command to search for the challenge:
   ```
   man -k /challenge/challenge
   ```
   The output indicated the randomized man page name:
   ```
   ftqhtrntti (1) - print the flag!
   ```

   I then accessed the man page using the name found in the previous step:
   ```bash
   man ftqhtrntti
   ```

   The man page revealed that the command would print the flag if called with the correct argument. I ran:
   ```
   /challenge/challenge --ftqhtr 098
   ```
   The output was:
   ```
   Correct usage! Your flag: pwn.college{E0f98StTq5htrDntGtiDxZWkztG.dZTM4QDLwQDN1czW}
   ```


![image](https://github.com/user-attachments/assets/7ab563b2-0b8b-4b58-a437-8537104898e2)
![image](https://github.com/user-attachments/assets/3de1b8dc-35d1-4875-9ca9-6a068404ed79)
![image](https://github.com/user-attachments/assets/69526695-5485-4990-853b-d0f9f8602bcc)
![image](https://github.com/user-attachments/assets/d85c89df-dad9-4f9a-8ffd-c4e26088c1b7)

## Helpful Programs

   I started by invoking the program with the `-h` argument to view the help documentation:
   ```
   /challenge/challenge -h
   ```

   I used the `-p` option to print the value necessary for the `-g` option:
   ```
   /challenge/challenge -p
   ```
   The output revealed:
   ```
   The secret value is: 862
   ```

   With the secret value in hand, I invoked the program again using the `-g` option:
   ```
   /challenge/challenge -g 862
   ```
   The program confirmed the correct usage and displayed the flag:
   ```
   Correct usage! Your flag: pwn.college{MPURUARoq8O6H2Ghc6ZK76DLANh.ddjM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/6329d7c7-79d5-4be3-aed3-341e9f726698)


## Help for Builtins
