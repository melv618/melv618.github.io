# Learn how to connect stealthily to local networks by protecting your hardware identity and avoid profiling by blue team defenses.

## Description
A red teamer should learn how to connect stealthily to local networks to simulate a real-world attack effectively. By protecting your hardware identity and avoiding profiling, you can bypass some blue team defenses, making your testing more realistic.

- **Operating System**
  - **Linux**
    
*In this lab, I am using a Debian/debian-based operating system, but feel free to use any distribution that has NetworkManager and systemd.*

 * * *

For demonstration purposes, my hostname will begin with 'kali' and with the following commands, we will attempt to blend in with the local network and avoid too much attention.

![image](https://github.com/user-attachments/assets/6b9ef794-676d-410c-b0ea-fe232b3a92ee)

**Current MAC Address:**

![image](https://github.com/user-attachments/assets/815b6fd1-bb5c-494b-aea7-6b0bd765c6a4)

## 1. Create a NetworkManager Configuration File
```
nano /etc/NetworkManager/conf.d/mac-randomize.conf:
```
![image](https://github.com/user-attachments/assets/9a90ad19-6e02-4071-976e-42edcdb95ce3)

### Add the following contents
```
[device]
wifi.scan-rand-mac-address=yes
[connection]
wifi.cloned-mac-address=random
connection.stable-id=${CONNECTION}/${BOOT}
```
![image](https://github.com/user-attachments/assets/b4a141ae-afcf-4ce8-93f8-c44027b676ba)

#### Restart NetworkManager
```
systemctl restart NetworkManager
```

## 2. Create Hostname Generator Shell Script
This following script we will create, will generate a new hostname based on the DESKTOP-XXXXXXX template observed on windows systems today. This will allow us blend in more with local networks as Windows is a very common operating systems across most desktops and laptops today.
