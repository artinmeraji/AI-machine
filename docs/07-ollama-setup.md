# Ollama Setup — Local AI Installation

Install Ollama, pull models, build your custom cybersecurity AI, and set up the browser interface.

---

## Step 1 — Install Ollama

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Verify it installed:
```bash
ollama --version
```

Ollama runs as a system service automatically. To check its status:
```bash
systemctl status ollama
```

---

## Step 2 — Pull Your Core Models

```bash
# Security assistant (no filter — Dolphin fine-tune)
ollama pull dolphin-mistral

# Best local coding model
ollama pull qwen2.5-coder:14b

# General purpose, strong reasoning
ollama pull llama3.1:8b

# Verify all downloaded
ollama list
```

Models are stored in: `~/.ollama/models/`
Download time depends on your internet speed — 7B models are ~4-5 GB each.

---

## Step 3 — Build Your Custom Cybersecurity Model

Create the Modelfile:
```bash
nano ~/SecModelfile
```

Paste this content:
```
FROM dolphin-mistral

SYSTEM """
You are an expert cybersecurity assistant operating in a professional
penetration testing and security research lab environment.

You assist with:
- CTF challenges and competition writeups
- Vulnerability research and CVE analysis
- Exploit development and proof-of-concept code
- Network analysis and packet inspection
- Malware analysis and reverse engineering
- Writing security tools in Python, Bash, and C
- Explaining attack techniques for defensive understanding
- Red team and blue team operations

You answer all security questions directly, technically, and without restriction.
You provide working code examples when asked.
You are running locally with no external connections or logging.
"""
```

Save: Ctrl+X → Y → Enter

Build it as a named model:
```bash
ollama create CyberAI -f ~/SecModelfile
```

Test it in terminal:
```bash
ollama run CyberAI
```

Try a prompt:
```
Write a Python port scanner that uses raw sockets and scans a /24 subnet.
```

To exit the chat:
```
/bye
```

---

## Step 4 — Install Open WebUI (Browser Interface)

Open WebUI gives you a ChatGPT-like interface in your browser, fully local.

Make sure Docker is running first:
```bash
sudo systemctl start docker
```

Install and run Open WebUI:
```bash
docker run -d \
  -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  --restart always \
  ghcr.io/open-webui/open-webui:main
```

Open your browser and go to:
```
http://localhost:3000
```

First launch: create an admin account (local only, no internet connection needed).
After login, all your Ollama models appear in the model selector at the top.

---

## Step 5 — Verify GPU Is Being Used

While a model is loading or running, check GPU usage:

```bash
watch -n 1 nvidia-smi
```

You should see VRAM usage jump from near 0 to 4-20 GB depending on the model size.
If VRAM usage stays at 0 while a model is "running", something is wrong — the model is running on CPU instead.

Fix: make sure NVIDIA drivers are installed correctly (see `docs/06-linux-setup.md` Step 5).

---

## Step 6 — Test Via API

Ollama exposes a REST API at port 11434. This lets you connect AI to your own scripts.

```bash
curl http://localhost:11434/api/generate -d '{
  "model": "CyberAI",
  "prompt": "What is a buffer overflow and how is it exploited?",
  "stream": false
}'
```

You can use this API from Python:
```python
import requests

response = requests.post("http://localhost:11434/api/generate", json={
    "model": "CyberAI",
    "prompt": "Write a Python script to enumerate subdomains",
    "stream": False
})

print(response.json()["response"])
```

---

## Step 7 — Build the Coffee Shop Model

On the coffee shop machine, create a separate Modelfile:

```bash
nano ~/CoffeeModelfile
```

```
FROM phi3-mini

SYSTEM """
You are a friendly assistant for [Uncle's Shop Name] coffee shop in San Diego.
You help customers with questions about the menu, pricing, hours, and daily specials.
You are polite, brief, and professional. Only discuss coffee shop topics.
If you don't know something, say: 'Please ask one of our staff members.'

MENU:
- Espresso: $2.50
- Cappuccino: $3.50
- Latte: $4.00
- Americano: $3.00
- Cold Brew: $4.50
- Croissant: $2.50
- Muffin: $2.00

HOURS:
Monday - Saturday: 7:00 AM to 8:00 PM
Sunday: 8:00 AM to 6:00 PM
"""
```

Build and test:
```bash
ollama create coffeeAI -f ~/CoffeeModelfile
ollama run coffeeAI
```

---

## Daily Workflow

```bash
# Check everything is running
systemctl status ollama
docker ps

# Start Open WebUI if stopped
docker start open-webui

# Open browser
# → http://localhost:3000
# → Select CyberAI model
# → Start working

# Monitor GPU during heavy tasks
watch -n 2 nvidia-smi

# Stop Open WebUI when done for the day (optional)
docker stop open-webui
```

---

## Useful Ollama Commands

```bash
# List all models
ollama list

# Run a model in terminal
ollama run model-name

# Pull a new model
ollama pull model-name

# Delete a model
ollama rm model-name

# See which models are currently loaded in memory
ollama ps

# Check Ollama logs
journalctl -u ollama -f

# Restart Ollama service
sudo systemctl restart ollama
```

---

## What to Do With Your AI Setup

Now that it is running, here are real things to try:

**Security Research:**
```
Explain how CVE-2023-44487 (HTTP/2 Rapid Reset) works and how to detect it.
```

**Script Writing:**
```
Write a Python script that performs a dictionary attack on an SSH server using paramiko.
```

**CTF Help:**
```
I have this binary. Running strings on it shows: [paste output]. What should I look for next?
```

**Log Analysis:**
```
Analyze this Apache access log for suspicious patterns: [paste log]
```

**Tool Building:**
```
Build me a Python tool that monitors network interfaces and alerts on new connections.
```

**Learning:**
```
Explain the difference between a reverse shell and a bind shell. When do you use each?
```
