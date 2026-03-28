# 🐉 Kali Linux VM Setup Cheatsheet

> A quick-reference guide for getting a fresh Kali Linux install up and running inside a virtual machine.

---

## 1. Prerequisites

| Item | Recommended |
|---|---|
| Host RAM | 8 GB minimum (16 GB recommended) |
| Disk Space | 40–80 GB free |
| Hypervisor | VMware Workstation / VirtualBox / Proxmox |
| Kali ISO | [kali.org/get-kali](https://www.kali.org/get-kali/) |

### Verify ISO integrity (SHA256)
```bash
sha256sum kali-linux-*.iso
# Compare against hash on kali.org
```

---

## 2. VM Configuration (Recommended Specs)

| Setting | Value |
|---|---|
| RAM | 4 GB (8 GB for heavy tools) |
| CPUs | 2 vCPUs (4 recommended) |
| Disk | 60 GB dynamically allocated |
| Network | NAT (default) or Bridged |
| Display | Enable 3D acceleration if available |
| USB | USB 3.0 controller |

> **Tip:** If using VirtualBox, install the **Guest Additions ISO** after setup for clipboard sharing, drag-and-drop, and better display resolution.

---

## 3. Installation Steps

1. Boot from the Kali ISO in your VM
2. Select **Graphical Install** (recommended for beginners)
3. Set language, location, and keyboard layout
4. Configure hostname (e.g., `kali`) and domain (leave blank if unsure)
5. Create a non-root user and strong password
6. Partition disk → choose **Guided – use entire disk**
7. Select **All files in one partition**
8. Choose desktop environment (XFCE is default and lightweight)
9. Install GRUB bootloader → Yes → select the virtual disk
10. Reboot and remove ISO from virtual drive

---

## 4. First Boot — Essential Updates

```bash
# Switch to root or use sudo throughout
sudo su -

# Full system update
apt update && apt full-upgrade -y

# Clean up
apt autoremove -y && apt autoclean
```

---

## 5. Install VMware / VirtualBox Guest Tools

### VirtualBox Guest Additions
```bash
apt install -y virtualbox-guest-x11
reboot
```

### VMware Tools (open-vm-tools)
```bash
apt install -y open-vm-tools open-vm-tools-desktop
reboot
```

---

## 6. Enable & Harden SSH

```bash
# Start and enable SSH
systemctl enable ssh --now

# Verify status
systemctl status ssh

# Optional: change default port (edit sshd_config)
nano /etc/ssh/sshd_config
# Set: Port 2222
# Set: PermitRootLogin no
# Set: PasswordAuthentication no  (after setting up key-based auth)

systemctl restart ssh
```

### Generate SSH Key Pair (on host)
```bash
ssh-keygen -t ed25519 -C "kali-vm"
ssh-copy-id -p 2222 user@<VM_IP>
```

---

## 7. Configure the Network

```bash
# Check IP address
ip a

# Check default route
ip r

# DNS test
nslookup google.com

# Static IP via NetworkManager (GUI) or edit:
nano /etc/network/interfaces
```

### Enable Promiscuous Mode (for packet capture)
```bash
ip link set eth0 promisc on
```

---

## 8. Install Commonly Used Tool Groups

```bash
# Full Kali metapackage (WARNING: very large ~15 GB)
apt install -y kali-linux-everything

# Recommended balanced set
apt install -y kali-linux-default

# Top 10 tools only (minimal)
apt install -y kali-tools-top10

# Specific categories
apt install -y kali-tools-web          # Web app testing
apt install -y kali-tools-wireless     # WiFi/802.11
apt install -y kali-tools-forensics    # Forensics & imaging
apt install -y kali-tools-exploitation # Exploitation frameworks
apt install -y kali-tools-sniffing-spoofing  # Packet capture
```

---

## 9. Key Tools Quick Reference

| Tool | Purpose | Command |
|---|---|---|
| `nmap` | Network scanning | `nmap -sV -A <target>` |
| `metasploit` | Exploitation framework | `msfconsole` |
| `burpsuite` | Web proxy / testing | `burpsuite` |
| `wireshark` | Packet capture | `wireshark` |
| `aircrack-ng` | WiFi auditing | `airmon-ng start wlan0` |
| `hydra` | Brute-force logins | `hydra -l user -P list.txt ssh://target` |
| `john` | Password cracking | `john --wordlist=rockyou.txt hash.txt` |
| `gobuster` | Directory fuzzing | `gobuster dir -u http://target -w wordlist.txt` |
| `nikto` | Web server scanner | `nikto -h http://target` |
| `sqlmap` | SQL injection testing | `sqlmap -u "http://target?id=1" --dbs` |

---

## 10. Update Wordlists (rockyou.txt etc.)

```bash
# Wordlists are stored in /usr/share/wordlists/
ls /usr/share/wordlists/

# Decompress rockyou.txt if not already done
gunzip /usr/share/wordlists/rockyou.txt.gz

# Install SecLists (large community wordlist collection)
apt install -y seclists
ls /usr/share/seclists/
```

---

## 11. Snapshot Best Practices

| When | Why |
|---|---|
| After clean install + updates | Clean baseline restore point |
| Before installing new tool sets | Rollback if things break |
| Before any penetration test lab | Preserve pristine state |
| After major configuration changes | Track known-good states |

> Always take a **snapshot before** any significant change — not after.

---

## 12. Useful Kali-Specific Commands

```bash
# List all available Kali metapackages
apt-cache search kali-linux

# Check current Kali version
cat /etc/os-release

# Update Kali rolling release
apt update && apt dist-upgrade -y

# Launch Kali undercover mode (mimics Windows 10 UI)
kali-undercover

# Change desktop environment
update-alternatives --config x-session-manager
```

---

## 13. Networking Modes Cheatsheet

| Mode | Use Case | Host Access | Internet |
|---|---|---|---|
| **NAT** | Default, easy internet | Via port forward | ✅ |
| **Bridged** | Appears on LAN, full access | ✅ Direct | ✅ |
| **Host-Only** | Isolated lab, no internet | ✅ | ❌ |
| **Internal** | VM-to-VM only | ❌ | ❌ |

---

## 14. Security Reminders

- ⚠️ **Only use Kali tools against systems you own or have explicit written permission to test.**
- Change default credentials immediately (`kali` / `kali`)
- Disable SSH if not needed: `systemctl disable ssh`
- Use a VPN before any external testing engagement
- Keep tools and the OS updated regularly

---

## 15. Quick Troubleshoot

| Problem | Fix |
|---|---|
| No internet in VM | Check NAT/Bridged setting; restart NetworkManager |
| Screen too small | Install Guest Additions; set resolution in Display settings |
| Tool not found | `apt install -y <toolname>` or check `kali-tools-*` packages |
| SSH refused | `systemctl start ssh` and check firewall with `ufw status` |
| Slow performance | Increase RAM/vCPUs; disable desktop effects |
| Clipboard not working | Reinstall Guest Additions; enable bidirectional clipboard in VM settings |

---

*Generated for Kali Linux Rolling Release — [kali.org](https://www.kali.org)*
