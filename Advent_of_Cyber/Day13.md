# Day 13: It came without buffering! It came without lag!

**Connection to the Machine:**
To begin, a virtual machine and AttackBox were utilized for the analysis.

## Approach:

- Navigated to http://10.10.14.97 (enabled proxy to Burp).
- Opened Burp Suite and enabled the proxy intercept.
- Clicked the `Track` button on the browser. Burp Proxy intercepted the WebSocket traffic.
- Changed the value of the `userId` parameter from `5` to `8` and clicked the `Forward` button.

![image](https://github.com/user-attachments/assets/73a2c3ba-4492-4827-adc2-baf67d65f9f4)

- The flag appeared in the `Community Reports` in the browser.

![image](https://github.com/user-attachments/assets/90aa2a9d-14c0-4cca-a578-5a71af0ecfbb)

- In order to obtain the second flag, we had to post a message using a different user ID, as Mayor Malware, whose ID was previously revealed to be `8`.
- Opened Burp Suite and enabled the proxy intercept.
- Typed a message and clicked the `Send` button on the browser. Burp Proxy intercepted the WebSocket traffic.
- Changed the value of the `sender` parameter from `5` to `8` and clicked the `Forward` button.

![image](https://github.com/user-attachments/assets/7e8dad4f-202e-486f-9218-ed6d11c917d4)

- The flag appeared in the `Community Reports` in the browser.

![image](https://github.com/user-attachments/assets/8d166099-440d-419e-ae5b-f48e76accd0e)

---

## Answers to the given questions:

What is the value of Flag1?

```
THM{dude_where_is_my_car}
```

---

What is the value of Flag2?

```
THM{my_name_is_malware._mayor_malware}
```

---

![image](https://github.com/user-attachments/assets/fa981d83-1cce-4bd0-b2d2-41abdf5cbcdf)
