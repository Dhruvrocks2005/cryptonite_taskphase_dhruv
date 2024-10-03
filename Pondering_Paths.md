# Pondering Paths

Second Module

## The Root

Invoked the `pwn` program using its absolute path.

![image](https://github.com/user-attachments/assets/b09eb60a-0a37-4254-a214-7460124808fb)

## Program and absolute paths

Invoked its absolute path by executing the `run` file that is in the `challenge` directory that is, in turn, in the `/` directory.

![image](https://github.com/user-attachments/assets/78454257-d92e-4f73-a92e-11fd74f225c3)

## Position thy self

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.
<br>/usr/share/doc/fontconfig directory is the required directory.

![image](https://github.com/user-attachments/assets/059753a2-f4c2-4ab4-96c0-cc60005dbb79)

## Position elsewhere
This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.
<br>/etc directory is the required directory.

![image](https://github.com/user-attachments/assets/4b6b50a3-2ef7-48e5-8c08-caa85764335f)

## Position yet elsewhere

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program.
<br>/usr/include directory is the required directory.

![image](https://github.com/user-attachments/assets/e158132c-0d33-4198-8e0e-bf409127c113)


## implicit relative paths, from /

Running `/challenge/run` from my current directory failed because I wasn’t in `/`
<br>I used `cd /` to change to the root directory
<br>Once in `/`, I successfully ran `challenge/run`

![image](https://github.com/user-attachments/assets/1b52b92c-0472-4b7d-9fce-5926c4f71baa)


## explicit relative paths, from /

Running `challenge/run` directly resulted in an error because I wasn’t in the `/` directory.
<br>Using the absolute path `/challenge/run` was incorrect since the challenge required a **relative path**:
   ```
Incorrect... You invoked this challenge with an absolute path.
   ```

After changing to the `/` directory (`cd /`), I needed to use a relative path explicitly starting with `.`:
   ```
   ./challenge/run
   ```

   Running `./challenge/run` successfully produced the flag:
   ```
   pwn.college{ARwfUsi2yzfaLveoVlNwIoo6A5C.dBTN1QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/e62b8455-ab42-46ae-8e08-48e1d67f67f0)


## implicit relative path

   I first tried to run the binary using an absolute path from my current directory:
   ```
   /challenge/run
   ```
   This failed since I wasn't in the `/challenge` directory.

   I used `cd /challenge` to navigate to the correct directory:
   ```
   cd /challenge
   ```

   Linux requires explicitly specifying the current directory with `.` when executing a program from it. I used:
   ```
   ./run
   ```
   This worked, and I received the flag:
   ```
   pwn.college{AJtT9gpOwS-_JkxVB0PCn1yrZvb.dFTN1QDLwQDN1czW}
   ```
   
![image](https://github.com/user-attachments/assets/172a54a4-a779-433a-8d91-d9af54e6bc1f)

## home sweet home

   I first tried using `~` (home directory shorthand) directly:
   ```
   /challenge/run ~
   ```
   This failed because `~` points to `/home/hacker`, which is a directory:
   ```
   /challenge/run: line 29: /home/hacker: Is a directory
   ```

   To satisfy the constraints, I used `~/a` to specify a file inside my home directory:
   ```
   /challenge/run ~/a
   ```
   This worked, and I received the flag:
   ```
   pwn.college{kkfDX_XckrZzJ7HWHs7SjdxdkhN.dNzM4QDLwQDN1czW}
   ```
   
![image](https://github.com/user-attachments/assets/5bd9d515-9cb3-4837-b99d-b5272a10ce79)
