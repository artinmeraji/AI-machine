# Linux Setup — Ubuntu + NVIDIA Drivers

---

## Why Ubuntu and Not Kali

Ubuntu 24.04 LTS is recommended as your main OS for this machine.

| | Ubuntu 24.04 LTS | Kali Linux |
|---|---|---|
| Stability | Rock solid for daily use | Designed for live boot/testing |
| AI tool support | Excellent | Works but more friction |
| NVIDIA driver install | Easy, one command | More manual work |
| Package availability | Massive ecosystem | Security-focused, smaller |
| Best for | Daily AI workstation | Pentesting boot drive |

**You can install all Kali tools on Ubuntu.** Run both worlds on one machine.
Use Ubuntu as your main OS. Boot Kali from USB when needed for specific tasks.

---

## Step 1 — Create Ubuntu USB Installer

Do this on another PC or laptop before building your machine.

```
1. Download Ubuntu 24.04 LTS Desktop from ubuntu.com
2. Download Balena Etcher (free, available for Windows/Mac/Linux)
3. Insert a USB drive (8 GB minimum — everything on it will be erased)
4. Open Balena Etcher
   → Select Image: your Ubuntu .iso file
   → Select Target: your USB drive
   → Click Flash
5. Wait 5-10 minutes for it to finish
6. USB is ready
```

---

## Step 2 — Boot From USB

```
1. Insert the USB into your new PC
2. Power on
3. Press F11 at startup — this opens the boot menu on MSI boards
4. Select your USB drive from the list
5. Ubuntu installer loads (takes 1-2 minutes)
```

---

## Step 3 — Install Ubuntu

```
[ ] Welcome screen: Select English
[ ] Keyboard layout: English (US)
[ ] Installation type: Normal Installation
[ ] Check: "Install third-party software for graphics and Wi-Fi"
    → This is important — installs NVIDIA drivers automatically

[ ] Disk setup: Erase disk and install Ubuntu
    → Select your NVMe SSD as the target drive
    → This erases the SSD and installs fresh — correct

[ ] Location: Los Angeles
    → San Diego uses the Los Angeles/Pacific timezone

[ ] Create your account
    → Your name: (anything)
    → Computer name: something like "cyberrig" or your name
    → Username: keep it short, lowercase, no spaces
    → Password: use a strong password — this machine runs security tools
    → Check: Require password to log in

[ ] Click Install Now
[ ] Wait 15-20 minutes

[ ] When done: click Restart Now
[ ] When prompted: remove the USB drive and press Enter
```

---

## Step 4 — First Boot and System Update

```bash
# Open Terminal (Ctrl + Alt + T)

# Update all packages
sudo apt update && sudo apt upgrade -y

# Restart to apply updates
sudo reboot
```

---

## Step 5 — Install NVIDIA Drivers

Ubuntu may have installed drivers automatically (if you checked third-party software).
Verify and install the latest:

```bash
# Check what GPU is detected
lspci | grep -i nvidia

# Check if driver is already installed
nvidia-smi
```

If `nvidia-smi` shows your GPU — drivers are already installed. Skip to Step 6.

If you get "command not found" or an error:

```bash
# Auto-install recommended driver
sudo ubuntu-drivers autoinstall

# Restart
sudo reboot

# Verify after restart
nvidia-smi
```

### What nvidia-smi Should Show

```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 545.xx.xx   Driver Version: 545.xx.xx   CUDA Version: 12.x      |
+-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
|   0  RTX 3090          Off   | 00000000:01:00.0  On |                  N/A |
+-------------------------------+----------------------+----------------------+
| 35%   42C    P8    18W / 350W |    320MiB / 24576MiB |      0%      Default |
+-----------------------------------------------------------------------------+
```

Key things to verify:
- GPU name shows correctly (RTX 3090)
- VRAM shows 24576 MiB (24 GB)
- Temperature shows (30-50°C at idle is normal)
- No error messages

---

## Step 6 — Install Essential Tools

```bash
# Core utilities
sudo apt install -y \
  curl \
  wget \
  git \
  htop \
  tmux \
  net-tools \
  build-essential \
  python3-pip \
  python3-venv \
  docker.io \
  ufw

# Start and enable Docker
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
newgrp docker

# Enable firewall (basic protection)
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow 3000  # Open WebUI
sudo ufw allow 11434 # Ollama API
```

---

## Step 7 — Install Security Tools

```bash
# Network and scanning tools
sudo apt install -y \
  nmap \
  wireshark \
  netcat-traditional \
  tcpdump \
  masscan \
  aircrack-ng

# Add yourself to wireshark group (capture without root)
sudo usermod -aG wireshark $USER

# Python security libraries
pip3 install \
  scapy \
  requests \
  pwntools \
  impacket \
  paramiko \
  cryptography

# Install Metasploit Framework
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall
chmod 755 msfinstall
sudo ./msfinstall
```

---

## Step 8 — Install Kali Tools on Ubuntu (Optional)

You don't need to run Kali to use Kali tools:

```bash
# Add Kali Linux repository to Ubuntu
echo "deb http://http.kali.org/kali kali-rolling main non-free contrib" | \
  sudo tee /etc/apt/sources.list.d/kali.list

# Add Kali GPG key
wget -q -O - https://archive.kali.org/archive-key.asc | sudo apt-key add -

# Update
sudo apt update

# Install specific Kali tools you want
sudo apt install -y sqlmap
sudo apt install -y gobuster
sudo apt install -y nikto
sudo apt install -y burpsuite
```

Or install the full Kali tool collection (large):
```bash
sudo apt install -y kali-tools-top10
```

---

## Step 9 — Verify Everything

```bash
# Check GPU
nvidia-smi

# Check RAM
free -h

# Check storage
df -h

# Check Docker is running
docker ps

# Check Python
python3 --version
pip3 --version

# Check git
git --version
```

All of these should respond without errors.

Proceed to `docs/07-ollama-setup.md` to install your AI.
