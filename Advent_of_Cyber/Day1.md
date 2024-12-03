# Day 1: Maybe SOC-mas music, he thought, doesn't come from a store?

**Connection to the Machine:**
To begin, a virtual machine and AttackBox were utilized for the analysis.

**Target Website:**
A YouTube-to-MP3 converter shared among SOC-mas organizers. Accessed the website by visiting `10.10.71.19` using the web browser from the Attackbox.

**File Analysis:**
After downloading a zip file via the site, two files were extracted: `song.mp3` and `somg.mp3`.

To determine the file's contents, ran the file and ExifTool commands on each one from the terminal.

It imports a file from `https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1` and executes the powershell command.

![image](https://github.com/user-attachments/assets/f511fa54-ea85-4a78-88fa-7e4e76f2adb4)

![image](https://github.com/user-attachments/assets/00ec68aa-6a7c-4e8f-a324-eee7815d1e33)

The PowerShell script contained a signature: `"Created by the one and only M.M."`  
A GitHub search for this phrase revealed repositories linked to the malicious actor.

---

## Answers to the given questions:

Ran "exiftool song.mp3" in the terminal to find out the author of the song

```
Tyler Ramsbey
```

![image](https://github.com/user-attachments/assets/7f5e1389-3542-4e81-b3bf-f9db61f9eb6d)

---

The malicious PowerShell script sends stolen info to a C2 server. What is the URL of this C2 server?

```
http://papash3ll.thm/data
```

![image](https://github.com/user-attachments/assets/5b6e260b-f521-4458-8fe0-b4f68ad66071)

---

Who is M.M? Maybe his Github profile page would provide clues?

```
Mayor Malware
```

![image](https://github.com/user-attachments/assets/c0d47c2a-96e7-4d92-a4b2-e8d192630dd7)

---

What is the number of commits on the GitHub repo where the issue was raised?

```
1
```

![image](https://github.com/user-attachments/assets/21baec77-11ca-4122-84ed-585bb6b2367f)

---

![image](https://github.com/user-attachments/assets/563ac91d-65f1-40bf-843b-5cfe9e285c8a)
