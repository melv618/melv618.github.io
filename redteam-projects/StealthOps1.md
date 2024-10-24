---
layout: default
title: Stealth Operations in a Hostile Server Environment
---

# Stealth Operations in a Hostile Server Environment

[GitHub Repository Link](#)

## Description
This scenario stimulates an enviroment where a red teamer SSHs into a hostile server and needs to achieve an objective while ensuring all actions are carried out without leaving traces or logs. Any investigation done on the server will be obstructed, simulating a stealthy red team operation.
Feel free to replicate this enviroment.

#### Technologies and Platforms Used
- Virtual Machines (VirtualBox)
  - Virtual Networking
*   Web Server (HTTP)
- Linux (Ubuntu)
  - SSH
  - SCP
  - Password Cracking

```
```
Topology Diagram
   +---------------------+
   |    Red Team Server  |
   |   (Wordlist & SSH)  |
   |                     |
   |  +---------------+  |
   |  |  wordlist.txt |  |
   |  +---------------+  |
   |         |           |
   |         |           |
   |  +----------------+ |
   | |extracted_flag.txt |
   |  +----------------+ |
   +---------------------+
             ^
             |
             |
             |
   +---------------------+
   | Victim  SSH Server  |
   |                     |
   |   +--------------+  |       +-----------------------+
   |   |  flag.txt   |   | ---- | Blue Team Investigators |
   |   +--------------+  |      | (Who we are hiding from)|
   |                     |      |                         |
   +---------------------+       +-----------------------+
             ^  
             |
             |
             |
   +---------------------+
   |   Red Teamer's PC   |
   |                     |
   |   (SSH Client)     |
   |                     |
   |   +--------------+  |
   |   |  Commands    |  |
   |   +--------------+  |
   +---------------------+
```
