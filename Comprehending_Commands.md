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

   The `ls` command is used to list files and directories. To find the renamed file, I executed the following command:
   ```
   ls /challenge
   ```
   The command listed:
   ```
   31803-renamed-run-11052  DESCRIPTION.md
   ```
   After identifying the renamed file, I ran it:
   ```
   /challenge/31803-renamed-run-11052
   ```
   This displayed the flag:
   ```
   pwn.college{oigSDiXiUvo8IWcMh85EoIm3mV3.dhjM4QDLwQDN1czW}
   ```
![image](https://github.com/user-attachments/assets/9cc59944-c55b-45e8-b1bd-54d78c5063a0)


## touching files

   First, I navigated to the `/tmp` directory:
   ```
   cd /tmp
   ```

   Using the `touch` command, I created the required files:
   ```
   touch pwn
   touch college
   ```

   To confirm the files were created, I listed the contents of `/tmp`:
   ```
   ls
   ```
   This showed:
   ```
   bin  college  hsperfdata_root  pwn  tmp.XvrUsDZh8M
   ```

   Finally, I executed the challenge:
   ```
   /challenge/run
   ```
   This provided the flag:
   ```
   pwn.college{AvFyJE7MDN1zIn-hqnJTw83Ww-P.dBzM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/37d8bdc2-1669-499e-93cb-015e1d640e9f)

## removing files

   First, I listed the files in my home directory:
   ```
   ls
   ```
   This showed:
   ```
   Desktop   a   delete_me  '~'
   ```

   I deleted the `delete_me` file using the `rm` command:
   ```
   rm delete_me
   ```

   I checked again to confirm that the file was deleted:
   ```
   ls
   ```
   The output now showed:
   ```
   Desktop   a  '~'
   ```

   Finally, I ran the checker to confirm the deletion:
   ```
   /challenge/check
   ```
   The output provided the flag:
   ```
   pwn.college{4EuHASRemgaxDXNGq56Jz6HI0JM.dZTOwUDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/06f89bfa-7cb7-4755-a352-f420fb62cba4)

## hidden files

   First, I changed the directory to the root (`/`):
   ```
   cd /
   ```

   I ran the `ls -a` command to list all files, including hidden ones (dot-prepended files):
   ```
   ls -a
   ```
   The output showed a hidden file named `.flag-145362971828456`.

   I used `cat` to read the contents of the hidden file:
   ```
   cat .flag-145362971828456
   ```
   The flag was revealed:
   ```
   pwn.college{426P1L6YC-slK-PkQlf2WfeH-wY.dBTN4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/d4eda794-cab7-4345-98d8-d17efced4c1f)

## An Epic Filesystem Quest

This was a file system exploration challenge where each clue led to a different directory, using commands like `ls`, `cd`, and `cat` to find hidden or trapped clues. 

   The journey started in `/` by finding and reading the `TRACE` file:
   ```
   cd /
   ls
   cat TRACE
   ```

Each clue directed to a new location. Some files were hidden (dot-prepended), requiring `ls -a`, while others were trapped, requiring `cat` without `cd`. I followed these steps:

   - `/usr/lib/debug/usr/lib/jvm/java-11-openjdk-amd64/.DISPATCH`
   - `/usr/share/racket/pkgs/math-lib/math/private/flonum/expansion/HINT`
   - `/usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/Latin/CUE-TRAPPED`
   - `/opt/radare2/test/unit/README-TRAPPED`
   - `/opt/linux/linux-5.4/include/config/pci/msi/irq/.DOSSIER`
   - `/opt/linux/linux-5.4/drivers/media/pci/mantis/NOTE`
   - `/usr/share/maxima-sage/5.42.2/share/contrib/maximaMathML/CLUE-TRAPPED`
   - `/opt/linux/linux-5.4/arch/mips/include/asm/SECRET`

   After a series of clues, the final `SECRET` file revealed the flag:
   ```bash
   pwn.college{U91ke09IRmFO7PZm5u71441ei6M.dljM4QDLwQDN1czW}
   ```

![image](https://github.com/user-attachments/assets/c1b1ad99-4648-49e7-aaf1-ec2c2d1254b2)
![image](https://github.com/user-attachments/assets/41d3c116-f68e-41a1-abb9-cfb180476fd2)
![image](https://github.com/user-attachments/assets/7c65351a-ac42-4ca1-aa67-3b7ab86cd27f)
![image](https://github.com/user-attachments/assets/7ac3b26e-11cf-4cb3-8407-699989257f6f)
![image](https://github.com/user-attachments/assets/dbc91d90-b29f-44bc-bedb-435ccfab14b1)

## making directories

The task was to create a directory `/tmp/pwn`, add a file called `college` in it, and then run `/challenge/run` to check the solution.

1. **Navigating to `/tmp`**:
   ```bash
   cd /tmp
   ```

2. **Creating the Directory**:
   ```bash
   mkdir pwn
   ```

3. **Adding the `college` File**:
   ```bash
   cd pwn
   touch college
   ```

4. **Running the Check**:
   ```bash
   /challenge/run
   ```
   This produced the flag:  
   `pwn.college{kjky4zmYJvnMBhngtWLOS2lFg-U.dFzM4QDLwQDN1czW}`


![image](https://github.com/user-attachments/assets/22350199-bb2a-4471-a5cc-f8c650713004)

## finding files


## linking files
