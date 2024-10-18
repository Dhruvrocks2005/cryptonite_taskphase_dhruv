# Processes and Jobs

Eighth Module

## Listing Processes

The task was to find the randomly named process in the `/challenge` directory using the `ps` command, and then relaunch it to obtain the flag.

- I used the `ps -ef` command to list all running processes:
   ```
   ps -ef
   ```

- From the output, I located the process:
   ```
   root          68       1  0 13:35 ?        00:00:00 /challenge/6893-run-27100
   ```

- I then relaunched the process using its full path:
   ```
   /challenge/6893-run-27100
   ```

Flag:
```
pwn.college{8QDBDvfiYdPiWSwJPFcgA6yowJp.dhzM4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/fb37bf64-784f-4f5a-8d06-7bf64d8638cf)

## Killing Processes

The task was to find and terminate the `/challenge/dont_run` process to allow the `/challenge/run` command to execute.

- I used the `ps -ef` command to list all running processes:
   ```
   ps -ef
   ```

- I located the `dont_run` process with PID 73:
   ```
   hacker        73      71  0 14:07 ?        00:00:00 /challenge/dont_run
   ```

- I used the `kill` command to terminate the process:
   ```
   kill 73
   ```

- After killing the process, I successfully executed:
   ```
   /challenge/run
   ```

Flag:
```
pwn.college{AK5lxQJzt9ZXY1hqdy40OnVpzPZ.dJDN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/d98dddb6-ecb8-406e-b280-6fb6001ef552)

## Interrupting Processes

The task was to interrupt the `/challenge/run` process to obtain the flag.

- I ran the command:
   ```
   /challenge/run
   ```

- I interrupted the process by pressing **Ctrl-C** in the terminal.

Flag:
```
pwn.college{ojKEYY-5UAzs9eRLxmeRZdcCuhP.dNDN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/fbd7b7d3-801e-46c4-9a07-3bd847a640fc)

## Suspending Processes

In this challenge, the goal was to suspend the `/challenge/run` process and launch another instance of it in the same terminal.

- I ran the command:
   ```
   /challenge/run
   ```

- I suspended the process by pressing **Ctrl-Z**. The terminal responded with:
   ```
   [1]+  Stopped                 /challenge/run
   ```

- I then launched another instance of the command:
   ```
   /challenge/run
   ```

Flag:
```
pwn.college{Al-5a4LshzwT_gbX_CC3o1yhvD9.dVDN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/54abfee6-00aa-463c-918e-ba757d6e3b8a)

## Resuming Processes

In this challenge, the goal was to suspend the `/challenge/run` process and then resume it using the `fg` command.

- I started by running the command:
   ```
   /challenge/run
   ```

- I suspended the process by pressing **Ctrl-Z**, which produced the output:
   ```
   [1]+  Stopped                 /challenge/run
   ```

- I resumed the suspended process using the `fg` command:
   ```
   fg
   ```

Flag:
```
pwn.college{MVFLM3fq-i_M0MjezmH49dx4-jM.dZDN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/c41576f7-3713-450d-a0ff-d223fd262b8e)

## Backgrounding Processes

In this challenge, the goal was to suspend the `/challenge/run` process, background it, and then launch another instance of the same process while the first was running in the background.

- I started by running the command:
   ```
   /challenge/run
   ```

- I suspended the process by pressing **Ctrl-Z**, resulting in:
   ```
   [1]+  Stopped                 /challenge/run
   ```

- I resumed the suspended process in the background using the `bg` command:
   ```
   bg
   ```

- I then launched another instance of the command:
   ```
   /challenge/run
   ```

Flag:
```
pwn.college{cfCQcJbJ498LLz8ImWCcGcBB1bl.ddDN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/781a05b2-5a57-4010-9f31-b877de31b03e)

## Foregrounding Processes

In this challenge, the objective was to suspend the `/challenge/run` process, background it, and then bring it back to the foreground without re-suspending it.

- I started the process by running:
   ```
   /challenge/run
   ```

- I suspended the process using **Ctrl-Z**, which resulted in:
   ```
   [1]+  Stopped                 /challenge/run
   ```

-  I resumed the suspended process in the background with the command:
   ```
   bg
   ```
   
- Finally, I brought the backgrounded process back to the foreground using:
   ```
   fg
   ```

Flag:
```
pwn.college{kI3f7Cw0zYm0AA-LKObX2G6YmMY.dhDN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/aa183c41-950e-499b-b860-fc0fd25c2c91)

## Starting Backgrounded Processes

In this challenge, the goal was to launch the `/challenge/run` process directly in the background by appending `&` to the command.

-  I launched the process in the background by appending an `&` to the command:
   
   ```
   /challenge/run &
   ```

Flag:
```
pwn.college{speGse8ej9B194vInLXQUCi3l7d.dlDN4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/3db1befa-f332-4c95-ac66-4ac27e08135e)

## Process Exit Codes

In this challenge, the objective was to retrieve the exit code returned by the command `/challenge/get-code` and then use that code as an argument for another command, `/challenge/submit-code`.

- I executed the command to get the exit code:
   ```
   /challenge/get-code
   ```
- The output indicated that the process exited with an error code.

- I accessed the exit code of the last command using the `$?` variable:
   ```
   echo $?
   ```
- The output was:
   ```
   249
   ```

- I then used the retrieved exit code as an argument for the submission command:
   ```
   /challenge/submit-code 249
   ```

Flag:
```
pwn.college{EbFwsQ1_E3DA-glpMs0WYfQcLP3.dljN4UDLwQDN1czW}
```


![image](https://github.com/user-attachments/assets/e844abbe-631e-4b0e-a271-4f4d55ffa310)
