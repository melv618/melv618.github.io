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
  - [Windows Server 2019 VHD](https://go.microsoft.com/fwlink/p/?linkid=2195334)

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
- **Images**:

## Screenshots
![Screenshot](png)

## Code Snippet
```python
# Example code
print("Hello, World!")
```
