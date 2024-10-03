# Comprehending Commands

Third module

## cat: not the pet, but the command!

   Since the flag was copied to the `flag` file in my home directory, I simply ran:
   ```
   cat flag
   ```
   This displayed the flag:
   ```
   pwn.college{oGOmcM19a71p6rrIcDUgLmq2l7H.dFzN1QDLwQDN1czW}
   ```
![image](https://github.com/user-attachments/assets/3a8acf22-6f44-4974-92f8-0b816c1353bb)

## catting absolute paths

   I used the `cat` command with the absolute path to read the flag:
   ```
   cat /flag
   ```
   This command successfully displayed the flag:
   ```
   pwn.college{sp81Yo6lFiEEiV1_IY_69gwJaLy.dlTM5QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/d0b6d028-c9e2-4930-b2bb-366f3ec7d8c5)

## more catting practice

   The challenge specified that I could not change directories using `cd`, making it necessary to access the flag using its absolute path directly.

   I executed the following command to read the flag:
   ```
   cat /lib/jvm/java-1.17.0-openjdk-amd64/flag
   ```
   This command successfully retrieved the flag:
   ```
   pwn.college{YBxyMZJf5OaP98SVqbOlEQBJdjW.dBjM5QDLwQDN1czW}
   ```
   
![image](https://github.com/user-attachments/assets/9582ad9c-452f-4deb-894d-d93bda78e405)

## grepping for a needle in a haystack

   To find the flag, I executed the following command:
   ```
   grep pwn.college /challenge/data.txt
   ```
   This command searched through the file and successfully retrieved the flag:
   ```
   pwn.college{AfYdonQrg_q50_v3FKZYzSumHck.ddTM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/7456b00e-08de-48f6-b3c8-d0aaa2282492)

## listing files


## touching files


## removing files


## hidden files


## An Epic Filesystem Quest


## making directories


## finding files


## linking files
