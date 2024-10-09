# Practicing Piping

Sixth Module

## Redirecting output

The objective was to redirect the output of the word "PWN" to a file named `COLLEGE`.

   - I used the `echo` command to print "PWN" and redirected the output to the file `COLLEGE`:

     ```
     echo PWN > COLLEGE
     ```
     
The output was successfully redirected, and the flag was obtained.

 Flag:
 
```
pwn.college{I9VY6QIIqD6vZgL6nGnqqkynKD_.dRjN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/cd789a51-8744-486d-bd66-8244a60258a7)

## Redirecting more output

The objective was to redirect the output of the `/challenge/run` command to a file named `myflag`.

   - I ran the following command to redirect the output:
     ```
     /challenge/run > myflag
     ```
   - The terminal continued to display informational messages, but the flag was written to the `myflag` file.

   - To check the contents of the file, I used the `cat` command:
     ```
     cat myflag
     ```

Flag:
```
pwn.college{Mr-Cgtkf1Y5vGNOjLge9PbjMbIq.dVjN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/38de52df-94f9-4a62-a7bc-f5106f428ebf)

## Appending output


The first half of the flag would be written directly to `/home/hacker/the-flag`, and the second half would be written to stdout. I had to append the second half to the file, using the `>>` operator to avoid overwriting the first half.

   - I used the append-mode redirection to ensure both halves of the flag were saved to the same file:
     
     ```
     /challenge/run >> /home/hacker/the-flag
     ```
     
   - I checked the contents of the file to confirm the full flag was saved:
     
     ```
     cat /home/hacker/the-flag
     ```
     
FLag:

```
pwn.college{Aox4AnIyyOk2GLdO9HjvpiO_ill.ddDM5QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/a321ba7c-72c2-430e-8eed-652e61034369)

## Redirecting errors

The objective was to redirect the output of `/challenge/run` to `myflag` and the error messages (instructions) to a file named `instructions`.

   - I ran the following command to redirect both outputs:
     ```
     /challenge/run > myflag 2> instructions
     ```
   - This command redirected standard output to `myflag` and standard error to `instructions`, ensuring nothing was printed to the terminal.

   - To check the instructions, I used:
     ```
     cat instructions
     ```
   - To check the flag, I used:
     ```
     cat myflag
     ```
 Flag:
```
pwn.college{wm5SypPHFRBfBb_vLc825HRrf3N.ddjN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/b606e58f-8e72-4709-a3ba-5b41412a8aa7)

## Redirecting input


### Challenge: Redirecting Input

The objective was to redirect the contents of the `PWN` file, which should contain the value `COLLEGE`, to the `/challenge/run` command using input redirection.

   - First, I created the `PWN` file containing the value `COLLEGE` using output redirection:
     ```
     echo COLLEGE > PWN
     ```

   - I then ran the `/challenge/run` command while redirecting input from the `PWN` file:
     ```
     /challenge/run < PWN
     ```

   - Upon successful execution, the command confirmed that it read the value `COLLEGE` from the file, and I received the flag.

 Flag:
```
pwn.college{sKM5nJkxDXJGDMjfRj64zwT5r6s.dBzN1QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/81490563-6a69-4996-b3c5-009eb70dd6db)

## Grepping stored results

The goal of this challenge was to redirect the output of the `/challenge/run` command to a file and then search for the flag within that file using `grep`.

   - I executed the `/challenge/run` command and redirected its output to the file `/tmp/data.txt`. This command generates a large amount of text, containing the flag among the lines:
     ```
     /challenge/run > /tmp/data.txt
     ```

   - After confirming that the output was successfully redirected, I used the `grep` command to search for the specific string that indicated the flag:
     ```
     grep pwn.college /tmp/data.txt
     ```

   - The command successfully returned the line containing the flag.

 Flag:
```
pwn.college{Aa5F5hqWKXcBvDZeZgBgpjHlnI2.dhTM4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/76e8d44a-55b0-491e-b14f-81e358d9acbb)

## Grepping live output

In this challenge, the objective was to use the pipe (`|`) operator to connect the output of the `/challenge/run` command directly into the `grep` command without needing to store the output in a file.

   - I executed the `/challenge/run` command and piped its output directly to `grep`, which searched for the string indicating the flag:
     ```
     /challenge/run | grep pwn.college
     ```

   - The command successfully filtered the output in real-time, displaying the line containing the flag.

 Flag:
```
pwn.college{AbvPGdJ3Kg9V757sOIi7kbzqZfi.dlTM4QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/b89e67db-ddc6-40be-b022-dad78d097b2c)

## Grepping errors

In this challenge, the objective was to filter the standard error output of the `/challenge/run` command using `grep`. Since standard error (fd 2) cannot be directly piped to another command, we used a two-step redirection process.

   - I used the `2>&1` operator to redirect standard error to standard output, allowing both outputs to be combined:
     ```
     /challenge/run 2>&1 | grep pwn.college
     ```

   - The combined output from both standard output and standard error was then piped into `grep`, which searched for the string indicating the flag.

 Flag:
```
pwn.college{0tClRfKd1xd0ijF6su6rhLhspAv.dVDM5QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/d3f6de30-440f-47c2-9293-f4ed4405ce71)

## Duplicating piped data with tee

In this challenge, the goal was to use the `tee` command to intercept data flowing from the `/challenge/pwn` command to the `/challenge/college` command. This was necessary to discover the secret code required for successful execution.

   - The command was set up to pipe the output from `/challenge/pwn` into `tee`, which duplicated the output to a file named `output` and also allowed it to continue to `/challenge/college`.
   - The command executed was:
     ```
     /challenge/pwn | tee output | /challenge/college
     ```
     
   - When the above command was run, it provided a warning indicating that the output was being overwritten. However, the key output from `/challenge/pwn` needed to be examined to determine the secret code.

   - After inspecting the contents of `output`, the correct secret code was identified. The command was then re-executed with the appropriate secret code:
     ```
     /challenge/pwn --secret "k49M9h6W" | /challenge/college
     ```

 Flag:
```
pwn.college{k49M9h6Wlg6eHsAL9pvMKO0ExgM.dFjM5QDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/1daf2c8a-0446-4572-b160-eb0575328396)

## Writing to multiple programs

In this challenge, the objective was to duplicate the output from the `/challenge/hack` command simultaneously into the inputs of two other commands: `/challenge/the` and `/challenge/planet`. This was achieved using the `tee` command alongside process substitution.

   - The `>(command)` syntax creates a named pipe that connects the standard output of the specified command to the standard input of another command. In this case, it allows the output from `/challenge/hack` to be piped into both `/challenge/the` and `/challenge/planet`.

   - The command executed was:
     ```
     /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
     ```

   - The `/challenge/hack` command produced output that was read by `tee`, which then sent the output to both `/challenge/the` and `/challenge/planet` through the named pipes created by the process substitution.

- The challenge was successfully completed, with the output from `/challenge/hack` duplicated and sent to both commands as required.

Flag:
```
pwn.college{UsW8XA2jKahuuoqJzWqi5_wqnuP.dBDO0UDLwQDN1czW}
```

![image](https://github.com/user-attachments/assets/2f92ae64-2c3f-41f3-88d9-98c126d39c0c)

## Split-piping stderr and stdout
Here's the Markdown report for the challenge involving redirecting stdout to one program and stderr to another:

---

### Challenge: Redirecting Stdout and Stderr to Different Programs

In this challenge, the objective was to redirect the standard output (stdout) of the `/challenge/hack` command to the `/challenge/planet` program and the standard error (stderr) to the `/challenge/the` program without mixing the two streams.

   - The command executed was:
     ```
     /challenge/hack 2> >( /challenge/the ) > >( /challenge/planet )
     ```

     - `2>` redirects the stderr of `/challenge/hack` to a process substitution that points to `/challenge/the`.
       
     - `>` redirects the stdout of `/challenge/hack` to another process substitution that points to `/challenge/planet`.

   - By using `>(...)`, the output streams were directed to their respective programs without mixing stdout and stderr.


- The challenge was successfully completed, with stdout directed to `/challenge/planet` and stderr directed to `/challenge/the` as required.

Flag:
```
pwn.college{cmpRSCKwKU6Cl8I65OKKO9ucGYj.dFDNwYDLwQDN1czW}
```


![image](https://github.com/user-attachments/assets/b7213bc8-d627-49bd-8e47-1dfa94f430bc)

