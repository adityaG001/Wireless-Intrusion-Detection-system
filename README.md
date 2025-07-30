# Wireless Network Intrusion Detection and Response System (WIDRS)

WIDRS is a lightweight and affordable wireless intrusion detection and response system built using Kismet and Kali Linux on Raspberry Pi. It monitors wireless traffic in real-time, detects common wireless threats, and provides immediate alerting through the Kismet dashboard.

## 🔐 Project Functionality

- Detects:
  - **Deauthentication Attacks** (DoS)
  - **Fake Access Point Flooding**
  - **Evil Twin Attacks** (Rogue APs)
- Uses **Kismet** for packet sniffing and alerting
- Simulates wireless threats using another device with **Kali Live OS**
- Provides graphical dashboard with categorized alerts

## 🧰 Hardware Requirements

- Raspberry Pi 4 or 3 (used as monitoring system)
- External Wi-Fi Adapter (preferably Atheros AR9271 chipset)
- microSD card (16GB or 32GB) for Raspberry Pi
- USB Pendrive (8GB or larger) for Kali Live OS
- Computer with BIOS/UEFI (for attacker machine)

## 💻 Software Requirements

- **Kali Linux ARM** for Raspberry Pi (Monitoring Device)
- **Kali Linux Live ISO** for Attacker Device
- Tools:
  - Kismet
  - Airmon-ng (from Aircrack-ng)
  - MDK4
  - Airbase-ng
  - Wireshark or Tcpdump (optional for validation)

## 📁 Repository Contents

- `setup.md`: Complete step-by-step setup guide for both devices
- `commands.md`: All terminal commands used
- `report.pdf`: Final mini project documentation
- `screenshots/`: Screenshots from Kismet dashboard
- `LICENSE`: (Optional) License for code or usage
