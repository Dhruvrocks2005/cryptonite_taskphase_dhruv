# Day 2:  One man's false positive is another man's potpourri.

**Connection to the Machine:**
To begin, a virtual machine was utilized for the analysis.

## Step 1: Access Elastic SIEM  
- Logged into the Elastic SIEM using the provided credentials:  
  - **URL:** `https://LAB_WEB_URL.p.thmlabs.com`  
  - **Username:** `elastic`  
  - **Password:** `elastic`
  
![image](https://github.com/user-attachments/assets/5a8b7c0a-1732-4fba-8816-685cc914ac02)

- Set the time filter to **Dec 1, 2024, 0900–0930** and observed 21 events.

![image](https://github.com/user-attachments/assets/d5614f25-0fc9-4736-a49c-b9860472c95f)

---

## Step 2: Filter and Add Relevant Fields  
Added the following fields as columns to analyze the events:  
- `host.hostname`: Host machine name.  
- `user.name`: User responsible for the activity.  
- `event.category`: Event type.  
- `process.command_line`: Details of the PowerShell commands.  
- `event.outcome`: Outcome of the events.  

![image](https://github.com/user-attachments/assets/610503bf-d40b-4582-9392-35e953c8aebf)

---

## Step 3: Expand Timeframe and Correlate Events  
Expanded the time window to **Nov 29–Dec 1, 2024** for additional context:  
- Observed over 6800 events.  
- Noted a spike in failed login attempts from IP `10.0.255.1`.  
- Filtered events by `source.ip` and `user.name` to isolate activity linked to the `service_admin` account.

### Findings:  
- Brute-force attempts succeeded on Dec 1, 2024, granting access to `service_admin`.  
- PowerShell commands were executed immediately after successful authentication.

![image](https://github.com/user-attachments/assets/463dc00f-1575-4085-9eaf-3229307a2764)

---

## Step 4: Decode the Encoded PowerShell Command  

- **Encoded Command:**  
  ```
  SQBuAHMAdABhAGwAbAAtAFcAaQBuAGQAbwB3AHMAVQBwAGQAYQB0AGUAIAAtAEEAYwBjAGUAcAB0AEEAbABsACAALQBBAHUAdABvAFIAZQBiAG8AbwB0AA==
  ```  
- **Decoded Output:**  
  ```
  Install-WindowsUpdate -AcceptAll -AutoReboot
  ```
  
![image](https://github.com/user-attachments/assets/fdf77406-7411-4139-953a-b546e0a262dd)

---

## Answers to the given questions:

What is the name of the account causing all the failed login attempts?

```
service_admin
```

---

How many failed logon attempts were observed?

```
6791
```

![image](https://github.com/user-attachments/assets/cf2aad67-e9db-4cf2-aefe-e075c1070195)

---

What is the IP address of Glitch?

```
10.0.255.1
```

---

When did Glitch successfully logon to ADM-01? Format: MMM D, YYYY HH:MM:SS.SSS

```
Dec 1, 2024 08:54:39.000
```

![image](https://github.com/user-attachments/assets/b50adbac-b257-4531-98b0-efb3bf4cb093)

---

What is the decoded command executed by Glitch to fix the systems of Wareville?

```
Install-WindowsUpdate -AcceptAll -AutoReboot
```

![image](https://github.com/user-attachments/assets/8ea044c6-38f5-489a-91ea-9c0e6750963b)

---

![image](https://github.com/user-attachments/assets/f72feb4e-95b3-4dc9-9026-4352d7284205)

