# Day 4: I’m all atomic inside!

**Connection to the Machine:**
To begin, a virtual machine was utilized for the analysis.

Opened a PowerShell prompt as administrator and entered the following commands:

```
Get-Help Invoke-Atomictest.
```

![image](https://github.com/user-attachments/assets/91cd98fc-ad27-4b18-a90f-3e7c62266050)

```
Invoke-AtomicTest T1566.001 -ShowDetails
```

![image](https://github.com/user-attachments/assets/b0829552-a128-4aaa-9550-a2efbc797777)

![image](https://github.com/user-attachments/assets/b2ffbf34-5206-40a7-9539-2f0b6782e73c)

```
Invoke-AtomicTest T1566.001 -TestNumbers 1 -CheckPrereq
Invoke-AtomicTest T1566.001 -TestNumbers 2 -CheckPrereq
Invoke-AtomicTest T1566.001 -TestNumbers 1
Invoke-AtomicTest T1566.001 -TestNumbers 1 -cleanup
```

![image](https://github.com/user-attachments/assets/fda0f3b0-ea0e-467c-a11c-e6dff080b565)

**Clearing the Sysmon event log:**

- Opened `Event Viewer`.
- Navigated to `Applications and Services` => `Microsoft` => `Windows` => `Sysmon` => `Operational` on the left-hand side of the screen.
- Right-clicked `Operational` on the left-hand side of the screen and clicked `Clear Log` and then `Clear`.

```
Invoke-AtomicTest T1566.001 -TestNumbers 1
```

![image](https://github.com/user-attachments/assets/6dfd0d03-5b7a-41ed-9725-ff12e0b96eba)

![image](https://github.com/user-attachments/assets/7a26a16d-bb63-4152-9290-6497d4c9ea0f)

Opened `PhishingAttachment.txt`:

![image](https://github.com/user-attachments/assets/df597440-25a7-4080-b947-594ef1efc3ef)

Flag found:

```
THM{GlitchTestingForSpearphishing}
```

```
Invoke-AtomicTest T1566.001-1 -cleanup
```

![image](https://github.com/user-attachments/assets/7d541328-24d1-4d89-b128-8d5f48e84692)


---

## Answers to the given questions:

What was the flag found in the .txt file that is found in the same directory as the PhishingAttachment.xslm artefact?

```
THM{GlitchTestingForSpearphishing}
```

---

What ATT&CK technique ID would be our point of interest?

```
T1059
```

![image](https://github.com/user-attachments/assets/2eb01413-ee92-45ec-b142-99b452537e46)

---

What ATT&CK subtechnique ID focuses on the Windows Command Shell?

```
T1059.003
```

![image](https://github.com/user-attachments/assets/ed2cfe8a-31d4-4148-a0f7-de5b795241ff)

---

What is the name of the Atomic Test to be simulated?


```
Simulate BlackByte Ransomware Print Bombing
```

Command used:

```
Invoke-AtomicTest T1059.003 -ShowDetails
```

![image](https://github.com/user-attachments/assets/b4718f8a-ed97-4f32-86b8-82d9ef3ddcf7)
![image](https://github.com/user-attachments/assets/03a26645-b288-4ef4-aabb-88755d89688b)
![image](https://github.com/user-attachments/assets/d6217cd7-b2d1-42ef-bd2f-1c10a2554888)
![image](https://github.com/user-attachments/assets/bd864db3-5384-40c5-b7f9-1e4e713c3704)

---

What is the name of the file used in the test?

```
Wareville_Ransomware.txt
```
![image](https://github.com/user-attachments/assets/7964fb14-2edb-4c3c-9b34-316f3857a71f)

---

What is the flag found from this Atomic Test?

```
THM{R2xpdGNoIGlzIG5vdCB0aGUgZW5lbXk=}
```

Command used:

```
Invoke-AtomicTest T1059.003
```

![image](https://github.com/user-attachments/assets/b6c9a3f1-5b73-4202-837b-212b872355d5)

---

![image](https://github.com/user-attachments/assets/ad096564-bc3f-49da-a555-271406018546)
