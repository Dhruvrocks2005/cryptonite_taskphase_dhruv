# File Globbing

Fifth Module

## Matching with *


   - The `*` character acts as a wildcard, matching any string of characters in filenames, except for `/` or a leading `.`.
   - For example, `file_*` matches any file starting with `file_`.

 **Navigating to `/challenge`**:
   - Starting from the home directory, I used the globbing technique to change directories to `/challenge`:
   ```
   cd /c*
   ```
   This command matches the directory name and successfully changes the current working directory to `/challenge`.

 **Running the Challenge Command**:
   - After successfully changing to the `/challenge` directory, I executed the following command to retrieve the flag:
   ```
   /challenge/run
   ```
   The output confirmed that I ran the command with the correct working directory and provided the flag:
   ```
   You ran me with the working directory of /challenge! Here is your flag:
   pwn.college{E1TAMAQ9q7oT2x3hUIxPHSG-o5D.dFjM4QDLwQDN1czW}
   ```
![image](https://github.com/user-attachments/assets/bddbd621-4ac5-4e6a-a6e4-d72513e7aaf1)

## Matching with ?

   - The `?` character matches exactly one character in filenames.
   - For example, `file_?` matches any file that has one character after `file_`, such as `file_a` and `file_b`, while `file_??` matches files with two characters after `file_`, such as `file_cc`.

 **Navigating to `/challenge`**:
   - Starting from the home directory, I used the `?` wildcard to change directories to `/challenge` by substituting characters:
   ```
   cd /?ha??enge
   ```
   This command correctly matches the directory name and successfully changes the current working directory to `/challenge`.

 **Running the Challenge Command**:
   - After successfully changing to the `/challenge` directory, I executed the following command to retrieve the flag:
   ```
   /challenge/run
   ```
   The output confirmed that I ran the command with the correct working directory and provided the flag:
   ```
   You ran me with the working directory of /challenge! Here is your flag:
   pwn.college{EPr0HQGbqTYuc9ubvHup8AcQrZ9.dJjM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/56596df5-793c-4021-8865-2373ad9074ab)

## Matching with [ ]

   - The `[]` brackets match any one of the characters listed inside them.
   - For example, `file_[ab]` will match `file_a` or `file_b`, as it looks for either 'a' or 'b' after `file_`.

 **Navigating to the Challenge Directory**:
   - I first changed my working directory to `/challenge/files`:
   ```
   cd /challenge/files
   ```

 **Running the Challenge Command**:
   - I executed the following command to run the challenge and pass an argument that matches multiple files:
   ```
   /challenge/run file_[bash]
   ```
   This command correctly matched `file_b`, `file_a`, `file_s`, and `file_h` based on the bracket globbing.

 **Retrieving the Flag**:
   - The output confirmed the correct execution of the command, providing the flag:
   ```
   You got it! Here is your flag!
   pwn.college{wTDeAsYAa3Ku-D9f6Tmwgbc2eW5.dNjM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/f74f24e7-3634-46da-9ebe-b92a443d8509)


## Matching paths with [ ]

   - Starting from my home directory, I constructed the absolute paths to the required files in `/challenge/files` using bracket globbing:
   ```
   /challenge/run /challenge/files/file_[bash]
   ```
   This command correctly matched the paths to `file_b`, `file_a`, `file_s`, and `file_h`.
   
<br>

   - The output confirmed that the command executed successfully, and the flag was provided:
   ```
   You got it! Here is your flag!
   pwn.college{4zyen6rNqDjyq-zLSyliyG8Vmep.dRjM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/a060e31b-c05e-447e-a19e-95a69ad3664d)



## Mixing globs
The objective was to match the files `challenging`, `educational`, and `pwning` in `/challenge/files` using a short (6 characters or less) glob.

1. Navigated to the directory and listed files:
   ```
   cd /challenge/files
   ls
   ```
2. Identified that the target files started with `c`, `e`, and `p`.
3. Used the glob pattern `[cep]*` to match all three files:
   ```
   /challenge/run [cep]*
   ```

 Flag:
```
pwn.college{wNLT05uUSkWNf2PD4t65QK0VfJY.dVjM4QDLwQDN1czW}
```



![image](https://github.com/user-attachments/assets/fad219c1-9d38-449d-b385-f3402bfacb5d)

## Exclusionary globbing

The task was to run a glob that matches all files except those starting with `p`, `w`, or `n` in `/challenge/files`.


 **Forming the Glob**: 
   - I used the pattern `[!pwn]*` to exclude files starting with `p`, `w`, or `n`.

 **Executing the Command**:
   ```
   cd /challenge/files
   /challenge/run [!pwn]*
   ```

Flag:
```
pwn.college{MhfdxpxPt5jIVWVs5buzWdaqV-y.dZjM4QDLwQDN1czW}
```


![image](https://github.com/user-attachments/assets/84cb04ac-f9a5-4aba-b8b7-d78504bb954a)


