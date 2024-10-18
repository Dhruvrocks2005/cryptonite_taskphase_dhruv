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


## Permissions Setting Practice


## The SUID Bit

