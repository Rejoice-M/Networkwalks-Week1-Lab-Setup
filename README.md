# 🔐 Cybersecurity Lab Environment Setup (Week 1)

## 📌 Project Overview
This project focuses on setting up a safe, isolated virtual cybersecurity lab environment using Oracle VirtualBox and Kali Linux. The goal was to configure a private NAT Network, ensure full internet connectivity, and enable host-to-VM file sharing for future penetration testing and defensive labs.

## 🛠️ Tools & Technologies Used
*   **Hypervisor:** Oracle VirtualBox (v7.x)
*   **Attacker Machine OS:** Kali Linux (Pre-built VirtualBox Image)
*   **Network:** NAT Network (`10.0.0.0/24`)
*   **Utilities:** 7-Zip, Windows Command Prompt, Kali Terminal

## ⚙️ Key Configuration Steps
1.  **Virtualization Setup:** Installed VirtualBox and created a custom NAT Network (`10.0.0.0/24`) with DHCP enabled.
2.  **VM Import:** Downloaded the official Kali Linux `.7z` image, extracted it, and imported it into VirtualBox.
3.  **VM Tweaks:** 
    *   Allocated 2048 MB RAM.
    *   Enabled Bidirectional Shared Clipboard and Drag'n'Drop.
    *   Set Promiscuous Mode to "Allow All" (for future packet sniffing labs).
    *   Configured a Shared Folder (`/downloads`) mapping to the host Windows Downloads folder.
4.  **Static IP Configuration:** Modified the Kali network adapter (`Wired connection 1`) via `nmcli` to use the static IP `10.0.0.2/24` with Gateway `10.0.0.1`.
5.  **Snapshot:** Captured a clean snapshot of the working VM to serve as a restore point.

## 🚧 Challenges Faced & Troubleshooting

*   **Windows Defender False Positive:** The Kali `.7z` download was flagged as a virus. **Solution:** Verified the source (kali.org) and created a Windows Defender exclusion folder.
*   **Disk Space Exhaustion:** A 4GB download temporarily consumed 27GB due to browser caching and Defender quarantine. **Solution:** Ran Disk Cleanup and cleared temporary files.
*   **The "Invisible" Linux Password:** Terminal input appeared frozen during `sudo` commands. **Solution:** Learned that Linux hides password characters by default; typed the password blindly and pressed Enter.
*   **Network Activation Error:** The static IP failed to route initially. **Solution:** Manually defined the gateway (`10.0.0.1`) and DNS (`8.8.8.8`), and applied the `ipv4.dad-timeout 0` fix.
*   **University Firewall Blocking Ping:** `ping 8.8.8.8` showed 100% packet loss despite having internet. **Solution:** Identified that the university network blocks ICMP traffic; confirmed connectivity by loading Google in Firefox instead.

## 📸 Lab Evidence

<img width="959" height="560" alt="Screenshot 2026-10-29 030109" src="https://github.com/user-attachments/assets/0d12f710-d311-492b-bcf1-57bbe390cb2a" />

<img width="959" height="563" alt="Screenshot 2026-10-29 025649" src="https://github.com/user-attachments/assets/49e4d035-22d8-4e95-9e81-a8560bd10c8c" />

<img width="959" height="565" alt="Screenshot 2026-10-29 030125" src="https://github.com/user-attachments/assets/1024700b-ce4d-40ba-a8f5-2938c59c86bc" />

