# Day 17: He analyzed and analyzed till his analyzer was sore!

**Connection to the Machine:**
To begin, a virtual machine and the given direct link were utilized for the analysis.

Given link: https://10-10-93-214.p.thmlabs.com 

---

## Answers to the given questions:

Extract all the events from the cctv_feed logs. How many logs were captured associated with the successful login?

```
642
```

![image](https://github.com/user-attachments/assets/39be2a8d-d7c0-4c8c-b532-1b2160818982)

---

What is the Session_id associated with the attacker who deleted the recording?

```
rij5uu4gt204q0d3eb7jj86okt
```

![image](https://github.com/user-attachments/assets/f7799245-4845-4de0-adb1-ba6b8b1a98ae)

---

What is the name of the attacker found in the logs, who deleted the CCTV footage?

```
mmalware
```

The IP address `10.11.105.33` is associated with the session ID of the recording deletion.

Two more Session IDs were associated with this IP address:

![image](https://github.com/user-attachments/assets/2090ca72-c7f7-4a3b-a632-d8fe861f013f)

Both of these Session IDs were associated with the username `mmalware` in `cctv_feed`.

![image](https://github.com/user-attachments/assets/83e2478f-411a-41fc-8f46-3c5af0582729)
![image](https://github.com/user-attachments/assets/92dd0a05-fb30-462f-9ff6-72f5d5500665)

---

![image](https://github.com/user-attachments/assets/0d1b5127-157c-4327-a688-6f9ccdbac877)

