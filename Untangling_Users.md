# Untangling Users

Tenth Module

## Becoming root with su

In this challenge, the task was to use the `su` (switch user) command to elevate privileges to root and read the flag.

   - I initiated the `su` command to switch to the root user:
     
     ```
     su
     ```
   - I entered the root password, which was provided as `hack-the-planet`.
     
   - After successfully becoming the root user, I used the `cat` command to read the flag:
     
     ```
     cat /flag
     ```

Flag:
```
pwn.college{A-NpsIfhkXt5KURtmvueYFohaXA.dVTN0UDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/c684cf2b-1058-431c-8e99-52f26b35afae)

## Other users with su

In this challenge, the task was to switch to the `zardus` user using the `su` command and then execute the `/challenge/run` command to retrieve the flag.

   - I started by switching to the `zardus` user:
     
     ```
     su zardus
     ```
   - I entered the password for `zardus`, which was `dont-hack-me`.
     
   - After successfully switching to `zardus`, I executed the `/challenge/run` command:
     
     ```
     /challenge/run
     ```

Flag:
```
pwn.college{kx-M6_jvmYeazgPa-MYD0yHalps.dZTN0UDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/45e3e282-799c-4933-a69f-344df23574a6)

## Cracking passwords

In this challenge, the task was to crack a password from a leaked `/etc/shadow` file located in `/challenge/shadow-leak`, switch to the `zardus` user, and then run the `/challenge/run` command to retrieve the flag.

   - I started by using John the Ripper to crack the password hash:
     
     ```
     john /challenge/shadow-leak
     ```
   - After a brief period, I retrieved the cracked password for the `zardus` user, which was `aardvark`.
     
   - I then switched to the `zardus` user using the `su` command:
     
     ```
     su zardus
     ```
   - Upon entering the cracked password, I executed the command:
     
     ```
     /challenge/run
     ```

Flag:
```
pwn.college{c1fUYtBTbfucTBX0aKOej3N0ibS.ddTN0UDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/ecfa8b92-39ea-4b62-9167-857df28f1ce8)

## Using sudo

In this challenge, the task was to use `sudo` to read the flag located at `/flag`.

   - I executed the following command to read the contents of the flag file with elevated privileges:
     
     ```
     sudo cat /flag
     ```

Flag:
```
pwn.college{4H8J73cTjZs6jjzfgZxsxGdjZKB.dhTN0UDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/70a23763-ede9-436c-ab48-da1bd9eda64b)
