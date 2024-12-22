# Day 7: Oh, no. I'M SPEAKING IN CLOUDTRAIL!

**Connection to the Machine:**
To begin, a virtual machine was utilized for the analysis.

---

## Answers to the given questions:

What is the other activity made by the user glitch aside from the ListObject action?

```
PutObject
```

![image](https://github.com/user-attachments/assets/94dac6d4-1c47-47dd-924f-ad58654f1bc8)

---

What is the source IP related to the S3 bucket activities of the user glitch?

```
53.94.201.69
```

![image](https://github.com/user-attachments/assets/b624125a-dade-4f9f-98b1-de9457d7f72a)

---

Based on the eventSource field, what AWS service generates the ConsoleLogin event?

```
signin.amazonaws.com
```

![image](https://github.com/user-attachments/assets/9963850d-d09e-441f-b73d-abf130b4daea)

---

When did the anomalous user trigger the ConsoleLogin event?

```
2024-11-28T15:21:54Z
```

![image](https://github.com/user-attachments/assets/a78f7b5d-9000-4c71-b43d-7918508c1475)

---

What was the name of the user that was created by the mcskidy user?


```
glitch
```


---

What type of access was assigned to the anomalous user?

```
AdministratorAccess
```

![image](https://github.com/user-attachments/assets/949b5e83-2604-4465-9be8-a3e69a647d5e)

---

Which IP does Mayor Malware typically use to log into AWS?

```
53.94.201.69
```

![image](https://github.com/user-attachments/assets/004711a2-40a4-442e-91cc-1a044bc8b519)

---

What is McSkidy's actual IP address?

```
31.210.15.79
```

Command used:

```
q -r '["Event_Time","Event_Source","Event_Name", "User_Name","User_Agent","Source_IP"],(.Records[] | select(.userIdentity.userName=="mcskidy") | [.eventTime, .eventSource, .eventName, .userIdentity.userName // "N/A",.userAgent // "N/A",.sourceIPAddress // "N/A"]) | @tsv' cloudtrail_log.json | column -t -s $'\t' 
```

---

What is the bank account number owned by Mayor Malware?

```
2394 6912 7723 1294
```

Command used:

```
grep INSERT rds.log
```

![image](https://github.com/user-attachments/assets/c9efb083-9eb6-4e97-80da-c5a077c860c2)

---

![image](https://github.com/user-attachments/assets/3fd9dfed-a924-4d70-9e63-9ce56dff12e5)

