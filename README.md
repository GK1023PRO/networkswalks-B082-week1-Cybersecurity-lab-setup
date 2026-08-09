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
<img width="1365" height="718" alt="WhatsApp Image 2026-08-09 at 11 24 12 AM" src="https://github.com/user-attachments/assets/b3a6f741-2162-48b0-8283-0b39c466af08" />

`Phase-1-Kali-Base`

This snapshot provides a clean baseline for the following cybersecurity labs.
