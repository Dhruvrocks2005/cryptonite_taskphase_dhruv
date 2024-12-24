# Day 6: If I can't find a nice malware to use, I'm not going.

**Connection to the Machine:**
To begin, a virtual machine and RDP (Remote Desktop Protocol), using the TryHackMe VPN (OpenVPN), were utilized for the analysis.

---

`.\JingleBells.ps1` : This tool will run on the system and continuously monitor the generated Event Logs.

![image](https://github.com/user-attachments/assets/30a19468-b165-4b5d-bd85-15882aecd9b1)

After running the malware by navigating to `C:\Tools\Malware`, and double-clicking on `MerryChristmas.exe`, there was a popup by the EDR with a flag included.

![image](https://github.com/user-attachments/assets/96f9a178-e449-4895-8fc5-e0f4d8339574)

---

`floss.exe C:\Tools\Malware\MerryChristmas.exe |Out-file C:\tools\malstrings.txt`

This command scans for strings in the binary `MerryChrismas.exe` and saves the command results in a file called `malstrings.txt`.

![image](https://github.com/user-attachments/assets/b62e5572-a223-4175-8f28-6b2349395fc4)

Once the command is done, searching for the string `THM` in `malstrings.txt` gives the second flag.

![image](https://github.com/user-attachments/assets/aefb3f31-9ded-458c-a05b-96f1443fcb1b)

---

## Answers to the given questions:

What is the flag displayed in the popup window after the EDR detects the malware?

```
THM{GlitchWasHere}
```

---

What is the flag found in the malstrings.txt document after running floss.exe, and opening the file in a text editor?

```
THM{HiddenClue}
```

---

![image](https://github.com/user-attachments/assets/5def9332-b6e8-4c29-819f-94366f85c2cf)
