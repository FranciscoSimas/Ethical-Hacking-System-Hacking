# Ethical Hacking System Hacking Documentation

## Overview

This project involves setting up a network of virtual machines on AWS, using various operating systems, to demonstrate the use of Responder for capturing network authentication requests. The steps include setting up the machines, configuring necessary software, running Responder, and using John the Ripper to crack captured passwords.

## Prerequisites

- AWS Account
- Terminal Access (Terminus or any preferred terminal)
- RDP Client

## Setup Instructions

### Step 1: Create AWS Instances

Create four virtual machines (VMs) on AWS with the following operating systems:
1. Windows 11
2. Windows Server 2016
3. Ubuntu

### Step 2: Configure Ubuntu VM

1. **Update and Upgrade Ubuntu:**
   ```sh
   sudo apt update
   sudo apt upgrade
   ```

2. **Install XFCE Desktop Environment and Other Tools:**
   ```sh
   sudo apt install -y xfce4 xfce4-goodies
   sudo apt install -y xrdp chromium-browser filezilla
   ```

3. **Add Users to XRDP and SSL-Cert Groups:**
   ```sh
   sudo adduser xrdp ssl-cert
   sudo adduser [your_username]
   ```

4. **Login and Configure XRDP:**
   ```sh
   login [your_username]
   echo xfce4-session > ~/.xsession
   ```

5. **Access Ubuntu via RDP:**
   - Use an RDP client to connect to your Ubuntu VM using its public IP.

### Step 3: Access Other VMs

1. **Windows 11 and Windows Server 2016:**
   - Connect via RDP using their respective publicIPs.

2. **Ubuntu:**
   - Connect via SSH using their respective public IPs.

### Step 4: Set Up Responder on Ubuntu

1. **Clone Responder Repository:**
   ```sh
   git clone https://github.com/lgandx/Responder.git
   ```

2. **Create and Share a Folder via SMB:**
   ```sh
   sudo mkdir /home/simas/teste
   sudo net usershare add teste /home/simas/teste "A secret folder shared via SMB" everyone:F guest_ok=y
   ```

3. **Run Responder:**
   - Get the network interface name:
     ```sh
     ip a
     ```
   - Start Responder:
     ```sh
     sudo ./Responder.py -I [network_interface]
     ```

### Step 5: Access Ubuntu Shared Folder from Windows

1. **Open File Explorer on Windows VM:**
   - Enter `\\[Ubuntu_private_IP]` in the address bar to access the shared folder.

### Step 6: Analyze Logs and Crack Passwords

1. **Install John the Ripper on Ubuntu:**
   ```sh
   sudo snap install john-the-ripper
   ```

2. **Use John the Ripper to Crack Passwords:**
   ```sh
   sudo john [path_to_responder_log]
   ```

### Example Outputs

#### Responder Running
![Responder Running](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/91b6326c-a16f-4145-a4ab-a2d00512612a)

#### John the Ripper Cracking Passwords
![John the Ripper](https://github.com/FranciscoSimas/Ethical-Hacking-System-Hacking/assets/145347669/1f0eb0c5-9c25-45f2-806e-14600e50013e)

### Conclusion

By following these steps, you can set up a test environment to capture and analyze network authentication requests using Responder and crack the captured passwords using John the Ripper. This setup is useful for learning and demonstrating network security and penetration testing techniques.




