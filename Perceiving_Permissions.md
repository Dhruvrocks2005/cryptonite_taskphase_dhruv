# Perceiving Permissions

Ninth Module

## Changing File Ownership

In this challenge, the task was to change the ownership of the `/flag` file to the current user (`hacker`), and then read its contents.

- I executed the following command to change the ownership of `/flag` to the `hacker` user:
   ```
   chown hacker /flag
   ```

- After changing the ownership, I used the `cat` command to read the contents of the `/flag` file:
   ```
   cat /flag
   ```

Flag:
```
pwn.college{0EC6GI1vquwITYi-836MtpSJVm_.dFTM2QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/1793e1e5-3fad-4972-90ca-33204810eae9)

## Groups and Files
In this challenge, the task was to change the group ownership of the '/flag' file, making it accessible to the 'hacker' user group, and then read its contents.

   - I used the `chgrp` command to change the group ownership of the `/flag` file to `hacker`:
     
     ```
     chgrp hacker /flag
     ```
   - After changing the group, I used the `cat` command to read the flag:
     
     ```
     cat /flag
     ```

Flag:
```
pwn.college{Mlk9pSHk6thH2mFZzmIOJxlP-kk.dFzNyUDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/863da530-4974-48ee-a86f-2ced4f3d85bd)

## Fun With Groups Names

In this challenge, the task was to change the group ownership of the `/flag` file using a randomized group name assigned to my user and then read the flag.

   - I used the `id` command to find the group name associated with my user:

      ```
     id
     ```
   - After identifying the group (`grp16382`), I used the `chgrp` command to change the group ownership of the `/flag` file:
     
     ```
     chgrp grp16382 /flag
     ```
   - Finally, I used the `cat` command to read the flag:
     
     ```
     cat /flag
     ```

Flag:
```
pwn.college{c3hl_YBHwNVXXY-GAlf7ibOihTr.dJzNyUDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/f5384cd9-4ddb-4c26-92df-2ad583ee5bb4)

## Changing Permissions

In this challenge, the task was to modify the permissions of the `/flag` file to make it readable, despite being owned by `root`.

   - I used the `chmod` command to add read permissions for others (i.e., users who are not the owner or in the group):
     
     ```
     chmod o+r /flag
     ```
   - After modifying the permissions, I used the `cat` command to read the flag:
     
     ```
     cat /flag
     ```

Flag:
```
pwn.college{wkkeNjaRJiKhhxCluszLRZjGTZH.dNzNyUDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/7d2babd9-f617-4da6-bd8a-c05c841f7e8d)

## Executable Files

In this challenge, the task was to make the `/challenge/run` program executable and run it to retrieve the flag.

   - Initially, I used the `chmod` command to add execute permissions for others (`o+x`), but the permission was still denied:

      ```
     chmod o+x /challenge/run
     /challenge/run
     ```
   - Upon reviewing the file’s permissions, I noticed that the `hacker` user lacked execute access (I was the owner this time and did not fall into the others category), so I added execute permissions for the user (`u+x`):
     
     ```
     chmod u+x /challenge/run
     ```
   - After making the file executable, I successfully ran the program and retrieved the flag:
     
     ```
     /challenge/run
     ```

Flag:
```
pwn.college{gGrS2-swdfI8-7X7VmxVrsdeKd8.dJTM2QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/7035a5db-6534-4b7a-b577-667759d959e4)

## Permission Tweaking Practice

In this challenge, the task was to correctly modify the permissions of the `/challenge/pwn` file through eight rounds, following the specified permission requirements for each round. After successfully completing all rounds, I gained permission to modify the `/flag` file and read the flag.

- **Round 0:**
   - Needed permissions: `rwxr-xr-x`
   - Command used: 
     ```
     chmod ugo+x /challenge/pwn
     ```
![image](https://github.com/user-attachments/assets/5acc0996-d225-4e99-b2b0-fa65e6b39012)

- **Round 1:**
   - Needed permissions: `rwxrwxr-x`
   - Command used: 
     ```
     chmod g+w /challenge/pwn
     ```
![image](https://github.com/user-attachments/assets/9c5c893b-62c0-4648-baea-dbb48c961bfc)

- **Round 2:**
   - Needed permissions: `rwxrwxrwx`
   - Command used: 
     ```
     chmod o+w /challenge/pwn
     ```
![image](https://github.com/user-attachments/assets/929e9db9-f5ba-48bd-86c5-5ac26e55efb9)

- **Round 3:**
   - Needed permissions: `rw-rw-rw-`
   - Command used: 
     ```
     chmod ugo-x /challenge/pwn
     ```
![image](https://github.com/user-attachments/assets/532ce908-f2ea-4993-a575-0375bbf5cf9a)

- **Round 4:**
   - Needed permissions: `rw-rw--w-`
   - Command used: 
     ```
     chmod o-r /challenge/pwn
     ```
![image](https://github.com/user-attachments/assets/bf0de9c3-9a2b-4dc5-8284-9c80f333f8ab)

- **Round 5:**
   - Needed permissions: `rw-rw-rw-`
   - Command used: 
     ```
     chmod o+r /challenge/pwn
     ```
![image](https://github.com/user-attachments/assets/3a74911d-a24e-4e0d-a1f0-1a0f1ce1dde7)

- **Round 6:**
   - Needed permissions: `---rw----`
   - Command used: 
     ```
     chmod uo-rw /challenge/pwn
     ```
![image](https://github.com/user-attachments/assets/ba5f9b3a-2706-4b7a-b88d-8bf400a1d9b8)

- **Round 7:**
   - Needed permissions: `r--rw-r--`
   - Command used: 
     ```
     chmod uo+r /challenge/pwn
     ```
![image](https://github.com/user-attachments/assets/212d798a-8f61-40aa-b33d-aeb4d5a1e999)

---

**Final Step:**

After successfully completing all rounds, I was given permission to modify the `/flag` file:
   - Command used:
     ```
     chmod u+r /flag
     ```

   - Then I used the `cat` command to read the flag:
     ```
     cat /flag
     ```

Flag:
```
pwn.college{UOD3_CQ2AVJErlci-eud-TW8_Mq.dBTM2QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/203ce6a3-9b18-4b64-a125-fe89dcd46882)

## Permissions Setting Practice

In this challenge, the task was to modify the permissions of the `/challenge/pwn` file across multiple rounds, ultimately changing the permissions of the `/flag` file to allow for reading it.

- **Round 0:**
  - Current permissions of `/challenge/pwn`: `rw-r--r--`
    
  - Needed permissions: `r-xrwxrw-`
    
  - I set the permissions using:
    
    ```
    chmod u=rx,g=rwx,o=rw /challenge/pwn
    ```
![image](https://github.com/user-attachments/assets/3b89ea04-aa5b-4e19-9895-9e33397f666f)

- **Round 1:**
  - Current permissions: `r-xrwxrw-`
    
  - Needed permissions: `----w-r--`
    
  - I set the permissions using:
    
    ```
    chmod u=-,g=w,o=r /challenge/pwn
    ```
![image](https://github.com/user-attachments/assets/ae74d3aa-645c-493d-9ce7-4a4e9c49f96f)

- **Round 2:**
  - Current permissions: `----w-r--`
    
  - Needed permissions: `rwxr----x`
    
  - I set the permissions using:
    
    ```
    chmod u=rwx,g=r,o=x /challenge/pwn
    ```
![image](https://github.com/user-attachments/assets/cdb1c96d-cadd-461e-9f09-d72b59edcb86)

- **Round 3:**
  - Current permissions: `rwxr----x`
    
  - Needed permissions: `--x--xrwx`
    
  - I set the permissions using:
    
    ```
    chmod u=x,g=x,o=rwx /challenge/pwn
    ```
![image](https://github.com/user-attachments/assets/4d1154f2-7ea4-411c-bdb3-426458290b09)

- **Round 4:**
  - Current permissions: `--x--xrwx`
    
  - Needed permissions: `r--r---wx`
    
  - I set the permissions using:
    
    ```
    chmod u=r,g=r,o=wx /challenge/pwn
    ```
![image](https://github.com/user-attachments/assets/2cb30d8a-1fd9-419f-a533-7094df895efa)

- **Round 5:**
  - Current permissions: `r--r---wx`
    
  - Needed permissions: `r-xr----x`
    
  - I set the permissions using:
    
    ```
    chmod u=rx,g=r,o=x /challenge/pwn
    ```
![image](https://github.com/user-attachments/assets/2037fb2b-19c5-4f59-aa79-ce6f0d938c37)

- **Round 6:**
  - Current permissions: `r-xr----x`
    
  - Needed permissions: `-wx--x-wx`
    
  - I set the permissions using:
    
    ```
    chmod u=wx,g=x,o=wx /challenge/pwn
    ```
 ![image](https://github.com/user-attachments/assets/8479f3ab-a386-4ac1-9a17-e5fd71955f8c)

- **Round 7:**
  - Current permissions: `-wx--x-wx`
    
  - Needed permissions: `rwx--xrw-`
    
  - I set the permissions using:
    
    ```
    chmod u=rwx,g=x,o=rw /challenge/pwn
    ```
![image](https://github.com/user-attachments/assets/dbe0a28c-e440-4d0d-969b-722036f71618)

---

**Final Step:**
- The ownership of the `/flag` file was changed, and its current permissions were `---------`. I set it to be readable by the user:
  
  ```
  chmod u=r /flag
  ```
- I then read the flag:
  
  ```
  cat /flag
  ```

Flag:
```
pwn.college{8jWrowv-x-izNwMTTEqp2UeXY4D.dNTM5QDLwQDN1czW}
```
![image](https://github.com/user-attachments/assets/c65061d1-06a5-4b9f-b671-764aa2310481)


## The SUID Bit

In this challenge, the task was to add the SUID (Set User ID) bit to the `/challenge/getroot` program, allowing it to run with root privileges so that I could read the flag.

   - I first checked the permissions of the `/challenge/getroot` program:
     
     ```
     ls -l /challenge/getroot
     ```
   - I then added the SUID bit using the `chmod` command:
     
     ```
     chmod u+s /challenge/getroot
     ```
   - After setting the SUID bit, I confirmed the change:
     
     ```
     ls -l /challenge/getroot
     ```
   - Finally, I executed the program to gain a root shell:
     
     ```
     /challenge/getroot
     ```
   - In the root shell, I used the `cat` command to read the flag:
     
     ```
     cat /flag
     ```

Flag:
```
pwn.college{wRWa50e_-8fLOaM-weSgrkDaKIv.dNTM2QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/2084c0de-b884-4786-87ab-c7ae97ad3417)

