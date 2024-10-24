# Learn how to connect stealthily to local networks by protecting your hardware identity and avoid profiling by blue team defenses.

## Description
A red teamer should learn how to connect stealthily to local networks to simulate a real-world attack effectively. By protecting your hardware identity and avoiding profiling, you can bypass some blue team defenses, making your testing more realistic.

We also utilize automation for this process.

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
```bash
[device]
wifi.scan-rand-mac-address=yes
[connection]
wifi.cloned-mac-address=random
connection.stable-id=${CONNECTION}/${BOOT}
```
![image](https://github.com/user-attachments/assets/b4a141ae-afcf-4ce8-93f8-c44027b676ba)

#### Restart NetworkManager
```bash
systemctl restart NetworkManager
```

## 2. Create Hostname Generator Shell Script
The following script we will create, will generate a new hostname based on the DESKTOP-XXXXXXX template observed on Windows systems today. This will allow us blend in more with local networks as Windows is a very common operating systems across most desktops and laptops today.

### Travel to the system-wide scripts directory:
```bash
cd /usr/local/bin/
```
This directory is typically included in the system's PATH, so you can run the script from anywhere.

### Create the Script File
```
nano set-random-hostname.sh
```

![image](https://github.com/user-attachments/assets/7e8782d4-ced7-49fb-8e19-8986e9bce709)

### Add the following contents
```bash
#!/bin/bash
# Become root
[ "$UID" -eq 0 ] || exec sudo "$0" $@

# Generate random hostname in Windows format with 7 characters (letters and digits)
rnd=$(cat /dev/urandom | tr -dc '[:upper:][:digit:]' | fold -w 7 | head -n 1)

# Set the hostname
hostnamectl set-hostname "DESKTOP-$rnd"

# Overwrite hostname file
echo "DESKTOP-$rnd" > /etc/hostname
sed '/^127.0.1.1/d' < /etc/hosts > tmp$rnd
echo "127.0.0.1        DESKTOP-$rnd" >> tmp$rnd
cat tmp$rnd > /etc/hosts
rm tmp$rnd

```
![image](https://github.com/user-attachments/assets/b9e8472d-dd12-45be-98ed-7dcc566789fa)

#### Make the Script Executable
```bash
chmod +x set-random-hostname.sh
```

### Set the script to execute every time you connect to a new network
```bash
sudo nano /etc/NetworkManager/dispatcher.d/99-set-hostname
```

![image](https://github.com/user-attachments/assets/c07d02df-061d-40e8-876f-087933532616)

### Add the following contents
```bash
#!/bin/bash

# Check if the connection is up
if [ "$2" = "up" ]; then
    /usr/local/bin/set-random-hostname.sh
fi
```

![image](https://github.com/user-attachments/assets/16c3b4ea-098c-4388-92b9-a68a839bbc5f)

#### Make the Script Executable
```bash
sudo chmod +x /etc/NetworkManager/dispatcher.d/99-set-hostname
```
***
## Test your setup  

### Reboot your sytem
#### Connect to a network.

### Check your hostname
```bash
hostname
```
![image](https://github.com/user-attachments/assets/bc89346d-31c3-4492-8068-70b79d0a5aa5)

### New MAC Address:
```bash
ip link show | grep ether | awk '{print $2}'
```
![image](https://github.com/user-attachments/assets/1ecc4725-dc29-46d2-b701-ef69b366588d)

# Thank you for following along!
