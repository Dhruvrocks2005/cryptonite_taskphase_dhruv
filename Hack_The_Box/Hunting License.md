# Hunting License

I was given a binary called `license`:

![image](https://github.com/user-attachments/assets/3bfe36d4-1ec7-470d-9dc7-ea08c9e1eff9)

Disassembled it using `gdb`:

```
gdb /mnt/c/Users/dhruv/Downloads/Hunting\ License/rev_hunting_license/license
disassemble main
```

![image](https://github.com/user-attachments/assets/d3264696-bd9b-4e8f-b270-6f085e120618)

Listed the functions:

![image](https://github.com/user-attachments/assets/70d16504-ac1f-4eb4-84a5-06202065daa7)

Upon analyzing them, found that `exam` function is the one we are looking for:

![image](https://github.com/user-attachments/assets/c05f5141-4449-47b3-8ee1-39c1db56a670)
![image](https://github.com/user-attachments/assets/93dfab2a-a30e-4b84-893a-91efa7412acd)

Checked the contents of the strings:

![image](https://github.com/user-attachments/assets/a921ceef-773e-4dd1-bbaa-9dfbd103921b)

Set breakpoints at critical points, that is, `strcmp` calls and checked the arguments to `strcmp` ($rdi and $rsi):

![image](https://github.com/user-attachments/assets/1a5f7439-93e6-4bc2-a77d-a943a47c6eec)
![image](https://github.com/user-attachments/assets/0e98d0c1-f7b5-4676-a936-4d316608e1de)

Found all 3 passwords:

```
First: PasswordNumeroUno
Second: P4ssw0rdTw0
Third: ThirdAndFinal!!!
```

![image](https://github.com/user-attachments/assets/57e0a2a9-1156-46aa-a81e-b01bda08e346)

![image](https://github.com/user-attachments/assets/50b3eb03-c91a-48cf-8c30-49a09a27bccf)


**Flag:**

```
HTB{l1c3ns3_4cquir3d-hunt1ng_t1m3!}
```
