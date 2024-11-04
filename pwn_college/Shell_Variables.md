# Shell Variables

Seventh Module

## Printing Variables

In this challenge, the goal was to print the contents of the `FLAG` variable using the `echo` command.

   - Variables can be accessed using the `$` symbol.
   - The `FLAG` variable was printed using the following command:
     
     ```
     echo $FLAG
     ```
   - Upon executing the command, the shell printed out the value of the `FLAG` variable.
  
 Flag:
```
pwn.college{oVDqC4LAxAwTD-dax1MFqKy4NTF.ddTN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/923c1495-a3c4-41ff-b375-7ec7cfe709b5)

## Setting Variables

The goal of this challenge was to correctly set a variable named `PWN` to the value `COLLEGE` and retrieve the flag.

   - Variables can be assigned values using the `=` operator, with no spaces around it.

   - The following command was used to set the variable:
     ```
     PWN=COLLEGE
     ```
- The challenge was successfully completed, and the flag was retrieved.

Flag:
```
pwn.college{06OlAM9o60LlPQufNMZ9BR3iqw2.dlTN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/805bddda-f2dc-4d77-ab26-92b1cdf8ace7)

## Multi-word Variables

   - The shell treats spaces as delimiters between commands and arguments. Without quotes, multi-word assignments are split, causing issues.
   - To assign a value with spaces, the value must be enclosed in quotes.

   - The following command was used to set the variable:
     ```
     PWN="COLLEGE YEAH"
     ```
- The challenge was successfully completed, and the flag was retrieved.

Flag:
```
pwn.college{QsfOPZFAxhXeC7MF15zsNx-EP0X.dBjN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/7e6651ad-8e5a-415c-92da-d703c643b33a)

## Exporting Variables

The task was to:
1. Export the `PWN` variable so that the `/challenge/run` program inherits it.
2. Set the `COLLEGE` variable locally without exporting it.


  - The `COLLEGE` variable was set but not exported, so it remained local to the shell:
     ```
     COLLEGE=PWN
     ```

  - The `PWN` variable was set and exported, allowing child processes (like `/challenge/run`) to access it:
     ```
     export PWN=COLLEGE
     ```

 - The program `/challenge/run` was executed to check whether the environment was correctly set up:
     ```
     /challenge/run
     ```

- The challenge was successfully completed, and the flag was retrieved.

Flag:
```
pwn.college{othnksvmnBGnXM0fJxrvhGDKUNm.dJjN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/798835b9-bec8-4823-803d-10f13eb80cd9)

## Printing Exported Variables

The goal was to retrieve the `FLAG` environment variable and display it.
- I used the `env` command, which lists all exported environment variables, to locate the `FLAG`.

Command used:
```
env
```

The `FLAG` was successfully retrieved:
```
FLAG=pwn.college{kHCGAZVDaK_sGPGZkKR-rYObE5I.dhTN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/50b9adcb-0a44-4f4d-be53-196f9cd8c985)

## Storing Command Output

The task was to read the output of the `/challenge/run` command directly into a variable called `PWN`, which would contain the flag.

- I used command substitution to store the output of the `/challenge/run` command:

   ```
   PWN=$(/challenge/run)
   ```
- I then printed the value of the `PWN` variable:

   ```
   echo $PWN
   ```

Flag:
```
pwn.college{AVt05FO2CyTCdDAD3jAzK04nofa.dVzN0UDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/33c7a2c3-6d7d-435e-ae32-094f227ec36f)

## Reading Input

The task was to use the `read` command to set the variable `PWN` to the value `COLLEGE`.


- I executed the following command to read input and set the variable:
   ```
   read PWN
   ```
- I entered `COLLEGE` when prompted.

- After setting the variable, I obtained the flag.

Flag:
```
pwn.college{8AMFqoRP3hnX6o5Xe7dcPawGA5R.dhzN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/662d031b-f36b-4eac-9806-1096eddd3a3c)

## Reading Files

The task was to read the contents of the file `/challenge/read_me` into the environment variable `PWN`.


- I used the `read` command with input redirection to read the file directly into the variable:
   ```
   read PWN < /challenge/read_me
   ```

- After executing the command, I obtained the flag.

Flag:
```
pwn.college{AwsOO008GLBH9eL_CmuDwtY6JKt.dBjM4QDLwQDN1czW}
```


![image](https://github.com/user-attachments/assets/542b5382-af63-4ad3-a48e-5c1e6450b425)
