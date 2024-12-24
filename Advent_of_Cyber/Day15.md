# Day 15: Be it ever so heinous, there's no place like Domain Controller.

**Connection to the Machine:**
To begin, a virtual machine and RDP (Remote Desktop Protocol), using the TryHackMe VPN (OpenVPN), were utilized for the analysis.


---

## Answers to the given questions:

On what day was Glitch_Malware last logged in?

Answer format: DD/MM/YYYY

```
07/11/2024
```

![image](https://github.com/user-attachments/assets/dffa889d-8cd4-47b1-9475-58a5c79d5e7b)

11/07/2024 did not work so I tried 07/11/2024 and it worked

---

What event ID shows the login of the Glitch_Malware user?

```
4624
```

![image](https://github.com/user-attachments/assets/b12dd633-df9c-4b09-9839-2b4460f72e96)

![image](https://github.com/user-attachments/assets/db68aa9e-8577-4c46-9ab1-d3e65535ea0b)

---

Read the PowerShell history of the Administrator account. What was the command that was used to enumerate Active Directory users?

```
Get-ADUser -Filter * -Properties MemberOf | Select-Object Name
```

opened `%APPDATA%\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt`

![image](https://github.com/user-attachments/assets/8cf4ea2f-7423-49bd-9754-1312c9801e8c)

---

Look in the PowerShell log file located in Application and Services Logs -> Windows PowerShell. What was Glitch_Malware's set password?

```
SuperSecretP@ssw0rd!
```

![image](https://github.com/user-attachments/assets/7f535fe9-af8b-4638-8cc5-b83b4b55e02a)

---

Review the Group Policy Objects present on the machine. What is the name of the installed GPO?

```
Malicious GPO - Glitch_Malware Persistence
```

![image](https://github.com/user-attachments/assets/ff09b3d1-87a0-4ee9-be7e-a7b22501be47)

---

![image](https://github.com/user-attachments/assets/626a534c-2b4d-45a1-95bf-20843412faad)
