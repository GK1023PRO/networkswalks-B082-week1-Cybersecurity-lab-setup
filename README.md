# networkswalks-B082-week1-Cybersecurity-lab-setup
# Cybersecurity Labs

## Phase 1 — Kali Linux Setup

### Environment

- Virtualization: Oracle VirtualBox
- Operating System: Kali Linux
- Network Type: NAT Network
- NAT Network Name: CyberLab
- Network: 10.0.0.0/24

### Kali Linux Network Configuration

| Setting | Value |
|---|---|
| Interface | eth0 |
| IP Address | 10.0.0.10/24 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 10.0.0.1 |
| DNS | 8.8.8.8 |
| IPv4 Method | Static |

### Verification

The following connectivity tests were successful:

- `ping -c 4 10.0.0.1`
- `ping -c 4 8.8.8.8`
- `ping -c 4 google.com`

### Snapshot

A VirtualBox snapshot was created after completing Phase 1:
<img width="955" height="530" alt="Screenshot 2026-08-09 124508" src="https://github.com/user-attachments/assets/2d23f437-e3ef-49d6-bb83-5f339ae2ad92" />
<img width="959" height="538" alt="image" src="https://github.com/user-attachments/assets/734679d2-9ecb-452c-b1c2-a28a81bea9c4" />



`Phase-1-Kali-Base`

This snapshot provides a clean baseline for the following cybersecurity labs.
