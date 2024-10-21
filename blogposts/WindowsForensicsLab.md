---
layout: default
title: "Digital Forensics: Building a Windows Investigation Lab"
---

# Building a Windows Investigation Lab

## Description
The goal of this lab is to provide a hands-on environment for learning forensic techniques/tools, analyzing data, and understanding digital evidence handling in accordance with [NIST SP 800-86](https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-86.pdf).

_Create your own data/system to analyze using this investigation lab, starting with a simple “victim” VM and executing malware or simulating malicious user behavior:_
  - **Create a memory and disk image** of the "victim" system.
  - **Export the images** and import them to the forensic workstation.

## Technologies Used
- **Virtual Machines**
  - VirtualBox

- **Operating Systems**
  - Windows Server 2019 VHD
    - PowerShell
  - Ubuntu (WSL)
 
- **Forensic Tools**
  - Volatility
  - Log2Timeline
  - FTK Imager
  - KAPE

 * * *
## 1. Install Oracle VirtualBox
- **Description**: Download and install Oracle VirtualBox on your machine.
- **Extension Pack**: [Download here](https://www.virtualbox.org/)

## 2. Download ISO Files
- **Description**: Download the necessary ISO files.
  - [Windows Server 2019](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019)

## 3. Create Virtual Machine

### Windows Guest VM Setup
- **Description**: Set up the virtual machine using the Windows Server ISO file.

### VM requirements:
    - 100 GB disk – dynamically allocated.
    - 4+ GB RAM
    - 2 or more CPUs
    - NAT Networking Mode
    - Install VirtualBox Guest Additions
      - enable Drag & Drop, bi-directional clipboard, and folder sharing with the host in the VMs settings.
    - When finished, shut down the system and create a snapshot.
![Screenshot](https://github.com/melv618/melv618.github.io/blob/main/blogposts/images/windowsforensicslab/Screenshot%20from%202024-10-21%2002-54-06.png?raw=true)
![Screenshot](https://github.com/melv618/melv618.github.io/blob/main/blogposts/images/windowsforensicslab/Screenshot%20from%202024-10-21%2002-54-13.png?raw=true)
![Screenshot](https://github.com/melv618/melv618.github.io/blob/main/blogposts/images/windowsforensicslab/Screenshot%20from%202024-10-21%2002-54-58.png?raw=true)
  #### Install Windows Desktop Experience
  ![image](https://github.com/user-attachments/assets/862ff522-6c76-448e-b6b8-2e415740dd61)
  ![image](https://github.com/user-attachments/assets/a918d5a1-95e2-4e86-a5ac-6fc8b9f9e6d7)

  > #### When finished, shut down the system and create a snapshot.
  ![image](https://github.com/user-attachments/assets/40f7340f-e534-4e78-a7be-e057d1bfc897)

## 4. Enable Windows Subsystem for Linux (WSL) and Install Ubuntu

### Open PowerShell as Administrator and run the following command:
```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
![Screenshot from 2024-10-21 03-21-17](https://github.com/user-attachments/assets/a50aeb40-04a9-4a1e-842a-ef87e92fa12a)
![image](https://github.com/user-attachments/assets/85ec60b5-cffc-4d70-809b-f938bdad2218)

### Download Ubuntu 24.04 [here](https://wslstorestorage.blob.core.windows.net/wslblob/Ubuntu2404-240425.AppxBundle)
  > Rename the package from .AppxBundle to .zip and extract the archive
  ![image](https://github.com/user-attachments/assets/6969678d-0e40-42c6-a61c-2114fbc7a58e) 
  ![image](https://github.com/user-attachments/assets/230af256-097b-453d-8dd2-dc010c4eb12b)

  Install the x64.appx package contained within the archive using the following PowerShell command (as administrator!):
  ```
  Add-AppxPackage .\Ubuntu_2404.0.5.0_x64.appx
  ```
 ![Screenshot from 2024-10-21 03-35-35](https://github.com/user-attachments/assets/e2b77f4f-89ee-4d82-8d03-347f9790208f)

  Reboot the system
  
  Open “Ubuntu” in your Start Menu and set up a user account when asked.
  ![image](https://github.com/user-attachments/assets/95c079a1-3873-4272-9710-4ea7b4c90ee1)

  
## Code Snippet
```python
# Example code
print("Hello, World!")
```
