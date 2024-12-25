# Day 20: If you utter so much as one packet…

**Connection to the Machine:**
To begin, a virtual machine and RDP (Remote Desktop Protocol), using the TryHackMe VPN (OpenVPN), were utilized for the analysis.

- Opened the “C2_Traffic_Analysis” file on the Desktop (using Wireshark).

- We only need traffic coming from the IP address of Marta May Ware’s machine.
- Applied the filter: `ip.src == 10.10.229.217`.

![image](https://github.com/user-attachments/assets/f08e7fc5-452d-4137-bb9b-0c5dfe4b8d8f)

- The data we required was found in the highlighted packets conatining HTTP requests.

---

## Answers to the given questions:

What was the first message the payload sent to Mayor Malware’s C2?

```
I am in Mayor!
```

`POST /initial` packet:

![image](https://github.com/user-attachments/assets/ee5c676a-6e91-4857-b817-15e81f212b6d)

---

What was the IP address of the C2 server?

```
10.10.123.224
```

![image](https://github.com/user-attachments/assets/c250083a-4ffc-4840-95d9-38468badcc62)

---

What was the command sent by the C2 server to the target machine?

```
whoami
```

`POST /command` packet:

![image](https://github.com/user-attachments/assets/cee9b1a0-e285-47a7-b12d-ab24a1d9edba)

---

What was the filename of the critical file exfiltrated by the C2 server?

```
credentials.txt
```

`POST /exfiltrate` packet:

![image](https://github.com/user-attachments/assets/57a201d4-c772-4e97-9220-50edf37260f2)

---

What secret message was sent back to the C2 in an encrypted format through beacons?

```
THM_Secret_101
```

`POST /exfiltrate` packet:

![image](https://github.com/user-attachments/assets/f8d89ef9-0b1f-46a0-ac11-a0df6a7e14d7)

`POST /beacon` packet:

![image](https://github.com/user-attachments/assets/2c15bc14-cc14-41fd-85ae-94b9eb69d32c)

key: 1234567890abcdef1234567890abcdef

Encrypted: 8724670c271adffd59447552a0ef3249

AES ECB Decrytion:

![image](https://github.com/user-attachments/assets/58e920d3-070b-4873-af50-5f29c59a97f8)


---

![image](https://github.com/user-attachments/assets/ec852b07-8392-4e00-a735-b7cb2a42469f)
