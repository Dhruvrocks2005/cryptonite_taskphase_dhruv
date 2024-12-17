
# U ARe T Detective

Started with a `signal.sr` file, opened it in a hex editor and checked its magic number.

![image](https://github.com/user-attachments/assets/19ffd6a9-c4f4-4ef0-8de7-a38dd1f356a6)

It was corresponding with a zip file so saved it with a .zip and found a metadata file uponing opening it.

![image](https://github.com/user-attachments/assets/9b26a832-9c3f-4b2a-b809-29c6954c6172)

The metadata hinted towards the sigrok pulse view software.

![image](https://github.com/user-attachments/assets/b3aefc2b-2aaf-4d27-9b30-aba5e4e08994)

Found some signals in D1, from the name I guessed that we needed to use `UART decoder`.

But it was giving frame errors, so i figured out that we needed to change the baude rate.

According to the bit duration, which I found out to be `187.5 ns` , the baude rate came out to be `5333333`, which removed the frame errors.

Then i changed the data format to ascii and found the flag.

![image](https://github.com/user-attachments/assets/26592339-7217-4966-9d18-0f9b34d4a38c)


**Flag:**

```
nite{n0n_std_b4ud_r4t3s_ftw}
```
