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


## Interrupting Processes


## Suspending Processes


## Resuming Processes


## Backgrounding Processes


## Foregrounding Processes


## Starting Backgrounded Processes


## Process Exit Codes

