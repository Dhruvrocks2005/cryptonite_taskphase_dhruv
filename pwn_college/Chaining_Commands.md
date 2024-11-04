# Chaining Commands

Eleventh Module

## Chaining with Semicolons

In this challenge, the task was to chain two commands, `/challenge/pwn` and `/challenge/college`, using a semicolon.

   - I executed the following command to run both challenges in sequence:
     
     ```
     /challenge/pwn ; /challenge/college
     ```

Flag:
```
pwn.college{osH7249VN_ZWP6l-DpkrTar-E7I.dVTN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/b7e1f9c0-a5e3-4a8a-9180-b7a2b9372342)

## Your First Shell Script

In this challenge, the task was to create a shell script called `x.sh` that runs the commands `/challenge/pwn` and `/challenge/college`, then execute it.

   - I created the `x.sh` shell script with the following content:
     
     ```
     /challenge/pwn
     /challenge/college
     ```
   - After saving the script, I executed it using the command:
     
     ```
     bash x.sh
     ```

Flag:
```
pwn.college{wOEBckqAEYh_gL7-JqolIFWp5hi.dFzN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/b5b0f09e-69f9-4285-988f-f766b97bf4a3)

## Redirecting Script Output

In this challenge, the task was to create a script that runs the commands `/challenge/pwn` and `/challenge/college`, then pipes the output of the script into the `/challenge/solve` command.

   - I created the script `redscriptout.sh` with the following content:
     
     ```
     /challenge/pwn
     /challenge/college
     ```
   - I then executed the script and piped its output into the `/challenge/solve` command:
     
     ```
     bash redscriptout.sh | /challenge/solve
     ```

Flag:
```
pwn.college{AMFnYuyApEsVdxTeuKYWuQGb3Bc.dhTM5QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/3eb83deb-ad4a-4f4c-82cd-a3c46196fea2)

## Executable Shell Scripts

In this challenge, the task was to create a shell script that invokes the `/challenge/solve` command, make it executable, and run it without explicitly invoking bash.

   - I created the script `exeshellscript.sh` with the following content:
     
     ```
     /challenge/solve
     ```
   - I checked the file permissions of the script:
     
     ```
     ls -l exeshellscript.sh
     ```
   - I made the script executable using the `chmod` command:
     
     ```
     chmod u+x exeshellscript.sh
     ```
   - Finally, I executed the script directly:
     
     ```
     ./exeshellscript.sh
     ```

Flag:
```
pwn.college{4R4dcH3mHgCUHDk7uiixIJVRDw8.dRzNyUDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/d4b5b83a-9bf0-44d5-9d96-a2daf2db6a6f)
