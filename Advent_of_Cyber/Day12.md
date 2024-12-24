# Day 12: If I can’t steal their money, I’ll steal their joy!

**Connection to the Machine:**
To begin, a virtual machine and AttackBox were utilized for the analysis.

**Given:** account number: `101` and password: `glitch` 

**Task:** Attempt to exploit the vulnerability by transferring over $2000 from this account to the account number: `111`.

## Approach:

- Opened Burp Suite.
- Enabled `Allow Burp's browser to run without a sandbox` option from settings.
- Opened Burp's browser from the Proxy -> Intercept tab and went to the given URL: http://10.10.121.13:5000.
- Logged in using the given credentials and transferred an amount of $500 to the account number: `111`.
- Reviewed the fund transfer HTTP POST request logged in the Burp Suite's HTTP history option under the Proxy tab.
- Sent the POST request to `Repeater`.
- Duplicated the request inside the Repeater tab (5 requests so that $500 sent 6 times becomes $3000 which is more than the initial account balance of $2000).
- Created a tab to send the multiple requests simultaneously.
- Selected `Send group in parallel (last-byte sync)` and sent the requests.
- Received the flag when I navigated to the account in the browser.

![image](https://github.com/user-attachments/assets/dcd64b4b-4a1b-4474-836c-1251bb89b3ab)

![image](https://github.com/user-attachments/assets/9c9518b8-db0f-45d2-94cf-6ea01e075f0b)

---

## Answers to the given questions:

What is the flag value after transferring over $2000 from Glitch's account?

```
THM{WON_THE_RACE_007}
```

---

