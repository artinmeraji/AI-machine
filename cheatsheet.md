# Quick Reference Cheat Sheet

---

## Ollama

```bash
ollama serve                          # Start Ollama manually
ollama list                           # List all downloaded models
ollama pull model-name                # Download a model
ollama run model-name                 # Chat with a model in terminal
ollama rm model-name                  # Delete a model
ollama ps                             # See models loaded in memory
ollama create myModel -f ./Modelfile  # Build custom model
sudo systemctl restart ollama         # Restart Ollama service
journalctl -u ollama -f               # Watch Ollama logs live
```

---

## Open WebUI (Docker)

```bash
docker start open-webui               # Start the web interface
docker stop open-webui                # Stop it
docker restart open-webui             # Restart it
docker logs open-webui                # Check logs if something breaks
```

Open in browser: `http://localhost:3000`

---

## GPU Monitoring

```bash
nvidia-smi                            # GPU status snapshot
watch -n 1 nvidia-smi                 # Live update every second
watch -n 2 nvidia-smi                 # Live update every 2 seconds
```

---

## Ollama API (for scripting)

```bash
# Generate a response
curl http://localhost:11434/api/generate -d '{
  "model": "CyberAI",
  "prompt": "your prompt here",
  "stream": false
}'

# List models via API
curl http://localhost:11434/api/tags
```

Python:
```python
import requests
r = requests.post("http://localhost:11434/api/generate", json={
    "model": "CyberAI",
    "prompt": "your prompt",
    "stream": False
})
print(r.json()["response"])
```

---

## System Monitoring

```bash
htop                                  # CPU, RAM, process monitor
free -h                               # RAM usage
df -h                                 # Disk usage
lspci | grep -i nvidia                # Verify GPU detected
du -sh ~/.ollama/models/              # How much space models use
```

---

## Model Storage

```
Location:    ~/.ollama/models/
7B model:    ~4-5 GB
14B model:   ~8-9 GB
34B model:   ~20-22 GB
70B Q4:      ~38-42 GB
```

---

## Security Tools Quick Reference

```bash
nmap -sV -p- target-ip                # Full port scan with service detection
nmap -sC -sV target-ip                # Default scripts + version detection
wireshark                             # Open GUI packet analyzer
tcpdump -i eth0 -w capture.pcap       # Capture traffic to file
msfconsole                            # Start Metasploit
python3 -m http.server 8080           # Quick HTTP server in current dir
nc -lvnp 4444                         # Start netcat listener
```

---

## SSH

```bash
ssh user@ip                           # Connect to remote
ssh -i key.pem user@ip                # Connect with key file
ssh -L 8080:localhost:80 user@ip      # Local port forward
scp file.txt user@ip:/path/           # Copy file to remote
```

---

## Git

```bash
git clone url                         # Clone a repo
git status                            # What changed
git add .                             # Stage all changes
git commit -m "message"               # Commit
git push                              # Push to GitHub
git pull                              # Pull latest changes
```

---

## Model Recommendations — Quick Pick

| Task | Model |
|------|-------|
| Security research | `dolphin-mistral` |
| Writing exploit scripts | `qwen2.5-coder:14b` |
| Deep analysis | `nous-hermes2` |
| Coffee shop chatbot | `phi3-mini` |
| General questions | `llama3.1:8b` |
| Reading long files/logs | `mistral-nemo` |
