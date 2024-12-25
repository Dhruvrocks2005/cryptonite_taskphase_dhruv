# Day 14: Even if we're horribly mismanaged, there'll be no sad faces on SOC-mas!

**Connection to the Machine:**
To begin, a virtual machine and AttackBox were utilized for the analysis.

## Approach:

- To prevent any DNS logs, we had to resolve the Gift Scheduler’s FQDN locally on our machine:

```
echo "10.10.62.20 gift-scheduler.thm" >> /etc/hosts
cat /etc/hosts
```

![image](https://github.com/user-attachments/assets/05e9df60-a98d-4a3c-85d0-5288b977ba89)

- Navigated to https://gift-scheduler.thm. I could view the Certificate on the warning page.

- In Burp Suite, under proxy settings, added a new proxy listener with the listening port set to `8080` and the Specific address to the IP address of our AttackBox.

- Setting our machine as a gateway for all other Wareville’s machines:

```
echo "10.10.47.174 wareville-gw" >> /etc/hosts
cd ~/Rooms/AoC2024/Day14
./route-elf-traffic.sh 
```

![image](https://github.com/user-attachments/assets/28f0d51b-5e24-4c37-b2a8-6659070566c0)

- In the HTTP History tab in Burp Suite, we can see the POST requests containing clear-text credentials for the Gift Scheduler website.

---

## Answers to the given questions:

What is the name of the CA that has signed the Gift Scheduler certificate?

```
THM
```

![image](https://github.com/user-attachments/assets/5cffca6a-a0fb-43d4-b0d7-418402690d50)

---

Look inside the POST requests in the HTTP history. What is the password for the snowballelf account?

```
c4rrotn0s3
```

![image](https://github.com/user-attachments/assets/a85ed322-e2e9-40be-8704-c84bec26788f)

---

Use the credentials for any of the elves to authenticate to the Gift Scheduler website. What is the flag shown on the elves’ scheduling page?

```
THM{AoC-3lf0nth3Sh3lf}
```

![image](https://github.com/user-attachments/assets/6a8860df-15df-43cf-b524-ef12c256faaf)

---

What is the password for Marta May Ware’s account?

```
H0llyJ0llySOCMAS!
```

![image](https://github.com/user-attachments/assets/e5e0d8e0-bc18-4b57-a78a-21bfae27eca5)

---

What is the flag shown on the admin page?

```
THM{AoC-h0wt0ru1nG1ftD4y}
```

![image](https://github.com/user-attachments/assets/545409ee-d23b-439b-898d-f0e8fe925cca)

---


![image](https://github.com/user-attachments/assets/d99dcd77-671e-422a-8b73-bba4c1d8c47f)
