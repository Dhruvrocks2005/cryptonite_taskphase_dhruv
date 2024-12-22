# Day 10: He had a brain full of macros, and had shells in his soul.

**Connection to the Machine:**
To begin, a virtual machine and AttackBox were utilized for the analysis.

## Creating the Malicious Document:

![image](https://github.com/user-attachments/assets/13c3d5fe-c70a-4296-a3a9-8140007269ab)

![image](https://github.com/user-attachments/assets/45d1e265-af32-4883-96ac-161b7f6331aa)

![image](https://github.com/user-attachments/assets/b542f15e-8bf4-4a17-a78f-178baa9cd461)

![image](https://github.com/user-attachments/assets/eab02b38-2dbf-4136-8fb0-651f5ac7bd16)

## Listening for Incoming Connections:

![image](https://github.com/user-attachments/assets/b5fc48d0-0381-4691-9969-12d47d3b3f6f)

## Emailing the Malicious Document:

- went to http://10.10.136.14 
- used the given credentials to log in
- sent an email to the target user, `marta@socmas.thm`, with the malicious document attached

## Exploitation:

I got a reverse shell in some time and accessed the `flag.txt` file on the target system.

![image](https://github.com/user-attachments/assets/78863309-a169-4374-8d3d-46b629023b9e)

---

## Answers to the given questions:

What is the flag value inside the flag.txt file that’s located on the Administrator’s desktop?

```
THM{PHISHING_CHRISTMAS}
```

---

![image](https://github.com/user-attachments/assets/8c575d81-3f4d-4701-a7ba-db3e7c7a035b)

