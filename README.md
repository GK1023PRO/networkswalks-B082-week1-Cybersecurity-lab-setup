# networkswalks-B082-week1-Cybersecurity-lab-setup
# Cybersecurity Labs

📘 Networkwalks Internship - Phase 1: Kali Linux Setup
Intern ID: NW-0826-GZP
Domain: Cybersecurity
Date: 09/08/2026

📋 Table of Contents
Overview

Phase 1 Tasks

Step-by-Step Guide

Troubleshooting

Screenshots

Conclusion

📌 Overview
This document outlines the complete setup process for Kali Linux on VirtualBox as part of the Networkwalks Cybersecurity Internship program. Phase 1 focuses on creating a functional penetration testing environment.

🎯 Phase 1 Tasks
Step	Task	Status
1	Download & install 7-zip	✅
2	Download & install VirtualBox	✅
3	Configure NATNetwork (10.0.2.0/24)	✅
4	Download & import Kali Linux VM	✅
5	Setup IP configuration	✅
6	Take snapshot of the VM	✅
🛠 Step-by-Step Guide
Step 1: Download & Install 7-zip
Why? 7-zip is used to extract the Kali Linux VM files.

Go to: https://7-zip.org/download.html

Download the version compatible with your OS

Install with default settings

<img width="959" height="539" alt="Screenshot 2026-08-10 155513" src="https://github.com/user-attachments/assets/1fadbc7c-608e-4108-9ac5-2cc062015e75" />


Step 2: Download & Install VirtualBox
Why? VirtualBox allows us to run Kali Linux as a virtual machine on our host system.

Go to: https://virtualbox.org/wiki/Downloads

Download VirtualBox for your OS

Install with default settings

<img width="944" height="521" alt="Screenshot 2026-08-10 154640" src="https://github.com/user-attachments/assets/5c92a23c-7d14-4911-baac-421afaf3cbc8" />


Step 3: Configure NATNetwork in VirtualBox
Why? NAT Network allows multiple VMs to communicate with each other and the internet.

Instructions:

Open Oracle VirtualBox Manager

Go to File → Preferences → Network

Click the NAT Networks tab

Click the Add button ➕

Configuration:

text
Network Name: NatNetwork
Network CIDR: 10.0.2.0/24
Enable DHCP: ✅ Checked
Click OK to save

<img width="959" height="539" alt="Screenshot 2026-08-10 161404" src="https://github.com/user-attachments/assets/117059cc-f1e4-4cbf-9938-e87b3b84d832" />


Verify in VM Settings:

Select your Kali VM → Settings

Go to Network → Adapter 1

Set Attached to: → NAT Network

Set Name: → NatNetwork

Click OK

Step 4: Download & Import Kali Linux VM
Why? Kali Linux is the primary OS for penetration testing and cybersecurity tasks.

Go to: https://kali.org/get-kali

Download the VirtualBox image

Extract using 7-zip

Import Steps:

Open VirtualBox

Go to File → Import Appliance

Browse and select the .ova file

Click Next → Import

<img width="954" height="531" alt="Screenshot 2026-08-10 163117" src="https://github.com/user-attachments/assets/3aebb0e2-69aa-4ca2-9c62-dd48f54deed6" />

Step 5: Setup IP Configuration
Why? Proper IP configuration ensures network connectivity and communication with other VMs.

Method 1: Using dhcpcd (Kali 2026.2)

bash
# Check current IP
ip a

# Renew DHCP lease
sudo dhcpcd -k eth0
sudo dhcpcd eth0

# Verify IP
ip a
Expected Output:

text
eth0: <BROADCAST,MULTICAST,UP,LOWER_UP>
    inet 10.0.0.x/24  # Should be in 10.0.0.0/24 range
Method 2: Static IP Configuration (Optional)

bash
sudo nano /etc/network/interfaces
Add:

text
auto eth0
iface eth0 inet static
    address 10.0.0.100
    netmask 255.255.255.0
    gateway 10.0.0.1
bash
# Restart networking
sudo systemctl restart networking
DNS Configuration:

bash
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
echo "nameserver 1.1.1.1" | sudo tee -a /etc/resolv.conf
Test Connectivity:

bash
# Test IP connectivity
ping 8.8.8.8

# Test DNS resolution
ping google.com
<img width="957" height="520" alt="Screenshot 2026-08-10 171606" src="https://github.com/user-attachments/assets/a6187c51-ecdb-4898-9e15-3a0666d8810d" />


Step 6: Take Snapshot of the VM
Why? Snapshots save the current state, allowing you to revert if something breaks.

To Take a Snapshot:

With the VM running, go to Machine → Take Snapshot

Name it: Kali - Phase 1 Complete - Network Configured

Description: Base setup with working internet and DNS configuration

Click OK

<img width="959" height="539" alt="Screenshot 2026-08-10 172628" src="https://github.com/user-attachments/assets/a0d5212b-c9e6-416c-8ede-dcd263da13a9" />


🐛 Troubleshooting
Issue 1: "Temporary failure in name resolution"
Fix: Add DNS servers manually

bash
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
echo "nameserver 1.1.1.1" | sudo tee -a /etc/resolv.conf
Issue 2: "Destination Host Unreachable"
Fix: Flush old routes and renew DHCP

bash
sudo ip addr flush dev eth0
sudo ip route flush dev eth0
sudo dhcpcd -k eth0
sudo dhcpcd eth0
Issue 3: "dhclient: command not found"
Fix: Kali 2026.2 uses dhcpcd instead of dhclient

bash
# Instead of sudo dhclient eth0
sudo dhcpcd eth0

✅ Verification Checklist
□ 7-zip installed
□ VirtualBox installed
□ NATNetwork created (10.0.0.0/24)
□ Kali Linux imported
□ IP configuration verified (ip a shows 10.0.0.x)
□ Internet connectivity confirmed (ping google.com)
□ DNS resolution working
□ Firefox loads websites
□ Snapshot taken
□ Screenshots captured for each step
🎯 Conclusion
Phase 1 is now complete! The Kali Linux environment is fully functional with:

✅ Proper network configuration

✅ Internet connectivity

✅ Working DNS resolution

✅ Snapshot saved for future recovery

Next Steps: Proceed to Phase 2 - Install Windows 10/11 and test connectivity between all VMs.

📝 Notes
Kali Version: 2026.2

VirtualBox Version: 7.2.14

Host OS: SERVER2022

Network: NAT Network (10.0.2.0/24)

"Success is the sum of small efforts repeated day in and day out." - Robert Collier

📧 Contact: georgeskh003@hotmail.com
🔗 GitHub: github.com/GK1023PRO 
🏢 Networkwalks Internship 2026
