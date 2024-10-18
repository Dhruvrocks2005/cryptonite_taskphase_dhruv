# Pondering PATH

Twelfth Module

## The PATH Variable

In this challenge, the task was to disrupt the operation of the `/challenge/run` program by making it unable to find the `rm` command, preventing it from deleting the flag.

   - I cleared the `PATH` variable, which is used by the shell to locate commands:
     
     ```
     PATH=""
     ```
   - I then executed the `/challenge/run` command:
     
     ```
     /challenge/run
     ```

   - The output confirmed that the `rm` command could not be found:
     
     ```
     /challenge/run: line 4: rm: No such file or directory
     ```

Flag:
```
pwn.college{cOc-reBocKSqGoxIBR0-SdtZAMx.dZzNwUDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/a15cc865-a887-4e19-96ed-3332fa475ae9)

## Setting PATH

In this challenge, the task was to modify the `PATH` variable to include the directory `/challenge/more_commands/`, allowing the `/challenge/run` command to successfully invoke the `win` command using its bare name.

   - I updated the `PATH` variable to point directly to the required directory:
     
     ```
     PATH="/challenge/more_commands/"
     ```
   - I then executed the `/challenge/run` command:
     
     ```
     /challenge/run
     ```

   - The output confirmed that the `win` command was successfully invoked:
     
     ```
     Invoking 'win'....
     ```

Flag:
```
pwn.college{ImBzjO3LHY07rZnJrbXRRJ866ee.dVzNyUDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/9d9dc08d-1042-4a1b-997f-a5db08fb5dd0)

## Adding Commands

In this challenge, the task was to create a shell script called `win` that can read the contents of the flag file, and ensure that the `/challenge/run` command can find it by modifying the `PATH` variable.

   - I created the script `win` with the following content:
     
     ```
     cat /flag
     ```
   - I made the script executable:
     
     ```
     chmod u+x win
     ```
   - I checked the current `PATH` variable to determine where standard commands like `cat` could be found:
     
     ```
     echo $PATH
     ```
   - I updated the `PATH` variable to include the directories where system commands are located along with the directory where the `win` script is located:
     
     ```
     PATH="/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker"
     ```
   - Finally, I executed the `/challenge/run` command:
     
     ```
     /challenge/run
     ```

Flag:
```
pwn.college{wxdhRB3rEEAsW0QX_1Nw39HWQKX.dZzNyUDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/9d9f5c9d-23c7-4c35-abad-2aa9a8f88494)

## Hijacking Commands

