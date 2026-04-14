# Uncle's Coffee Shop Machine

**Budget:** $150-350
**Purpose:** Local AI assistant for menu Q&A, customer help, order guidance

---

## Key Difference From Your Machine

The coffee shop AI does NOT need to be powerful.
It needs to be **fast, reliable, quiet, and cheap.**

Customers ask simple questions:
- "What's in the latte?"
- "Do you have oat milk?"
- "What time do you close?"

A small 3B model answers these in 3-5 seconds. That is perfectly acceptable.
No GPU needed. No expensive parts. Just a used business PC.

---

## Recommended Setup

| Component | Pick | Price | Why |
|-----------|------|-------|-----|
| **Base Machine** | Used Dell OptiPlex 7060/7070/7080 Tower | $120-200 | Business-grade, quiet, reliable, low power, easy to maintain |
| **RAM** | 16 GB DDR4 | $20-40 if upgrade needed | Enough for small models + OS |
| **Storage** | 256 GB SSD | Usually included | Enough for OS + 2-3 small models |
| **GPU** | None | $0 | Not needed for small models on CPU |
| **Total** | | **$140-240** | |

---

## What to Search For

On Facebook Marketplace and Craigslist San Diego:

```
"Dell OptiPlex 7080"
"Dell OptiPlex 7070"
"Dell OptiPlex 7060"
"HP EliteDesk 800 G5"
"HP EliteDesk 800 G6"
"Lenovo ThinkCentre M720"
```

**What to look for in the listing:**
```
[ ] Says "Tower" or "MT" — NOT Mini, SFF, Micro, or Slim
[ ] 16 GB RAM (or 8 GB you can upgrade for $20)
[ ] Has an SSD
[ ] Intel i5 8th gen or newer (i5-8500, i5-9500, i5-10500)
[ ] Price: $100-200 is fair. Walk away above $220.
[ ] Powers on, working condition
```

---

## Minimum Specs

| Component | Minimum | Notes |
|-----------|---------|-------|
| CPU | Intel i5 8th gen | i5-8400 or better. Anything newer is fine. |
| RAM | 16 GB DDR4 | 8 GB works but 16 GB is better. $20 upgrade on Amazon. |
| Storage | 256 GB SSD | HDD is too slow. Must be SSD. |
| GPU | Not required | CPU inference at 5-10 tok/sec is fine for a chatbot |
| Network | Ethernet port | More reliable than WiFi for a business setting |

---

## Which AI Model to Run

| Model | Size | RAM Needed | Speed (CPU) | Best For |
|-------|------|-----------|-------------|---------|
| `phi3-mini` | 3.8B | 4 GB | 5-10 tok/sec | Best choice — fast, smart, tiny |
| `llama3.2:3b` | 3B | 3 GB | 6-12 tok/sec | Lightweight option |
| `mistral:7b` | 7B | 5 GB | 3-6 tok/sec | Smarter responses, slightly slower |

**Recommended: `phi3-mini`** — smallest, fastest, very capable for simple Q&A.

---

## Coffee Shop System Prompt

Create a `Modelfile` with your uncle's actual menu and info:

```
FROM phi3-mini

SYSTEM """
You are a friendly assistant for [Shop Name] coffee shop in San Diego.
You help customers with menu questions, pricing, hours, and specials.
You are polite, brief, and only discuss coffee shop topics.

MENU:
- Espresso: $2.50
- Cappuccino: $3.50
- Latte: $4.00
- Americano: $3.00
- Cold Brew: $4.50
- Croissant: $2.50
- Muffin: $2.00

HOURS:
Monday-Saturday: 7:00 AM - 8:00 PM
Sunday: 8:00 AM - 6:00 PM

If you don't know the answer, say: 'Please ask a staff member for help.'
"""
```

Build it:
```bash
ollama create coffeeAI -f ~/CoffeeModelfile
ollama run coffeeAI
```

---

## Serving It on the Shop's WiFi

Once Open WebUI is running, all devices on the same WiFi can access it:

```bash
# Find your local IP
ip addr show | grep "inet "
```

Then on any tablet, phone, or PC on the shop's WiFi:
```
http://192.168.x.x:3000
```

Put a tablet on the counter at this URL. Customers interact directly.

---

## Comparison: Your Machine vs Coffee Shop

| | Your Cybersecurity Rig | Coffee Shop Machine |
|---|---|---|
| **Budget** | $1,200-1,500 | $150-350 |
| **GPU** | RTX 3090 24GB | None |
| **RAM** | 32-64 GB | 16 GB |
| **Models** | Up to 70B | 3B-7B |
| **Speed** | 8-70 tok/sec | 3-12 tok/sec |
| **Power use** | 250-350W | 35-65W |
| **Noise** | Moderate | Very quiet |
| **Buy** | Mix new + used | All used |

---

## Phase 2 — Future Upgrades (Optional)

Once the basic chatbot works, you can expand:

- **Voice input** — customer speaks, AI responds (add a USB microphone)
- **Custom web app** — branded interface instead of Open WebUI
- **Order tracking** — connect to a simple POS or spreadsheet
- **Smart camera** — Raspberry Pi with AI HAT for counting customers
- **Offer to other shops** — once proven, replicate for other local businesses
