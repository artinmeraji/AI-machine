# Buying Guide — San Diego, California

Where to buy, what to pay, and how to avoid getting scammed.

---

## Where to Buy

### Local Stores — Walk In Same Day

| Store | What to Buy | Notes |
|-------|-------------|-------|
| **Micro Center — Tustin, CA** | Everything | ~1.5 hrs north. Best PC store in California. Buy CPU + Motherboard here for combo discount. |
| **Micro Center — Pacoima, CA** | Everything | ~2 hrs north (LA). Same quality as Tustin. |
| **Best Buy** | RAM, SSD, PSU, Case | Multiple SD locations: Mission Valley, Kearny Mesa, Chula Vista. Not great for GPU prices. |

> Micro Center combo deals: buying CPU + Motherboard together saves $20-50.
> Call ahead to check GPU stock before making the drive.

### Online — Ships to San Diego

| Site | Best For | Notes |
|------|----------|-------|
| **Amazon** | RAM, SSD, PSU, Case | Fast Prime shipping. Easy returns. |
| **Newegg** | New parts | Based in California — fast SD shipping |
| **B&H Photo** | GPU, premium parts | Reputable, competitive pricing |

### Used Parts — San Diego

| Source | Best For | Tips |
|--------|---------|------|
| **Facebook Marketplace SD** | Used GPUs, complete PCs | Most active. Search RTX 3060/3090. Meet safely. |
| **Craigslist San Diego** | Workstations, old PCs | Search HP Z440, Dell OptiPlex. Good deals. |
| **eBay** | Specific parts | 98%+ seller rating only. Check sold listings for real prices. |
| **r/hardwareswap** | Hobbyist parts | Reddit community. PayPal G&S only. |

---

## Fair Prices — San Diego Market 2025-2026

Use these when negotiating. Walk away if seller won't come close.

| GPU | VRAM | Fair Used Price | Notes |
|-----|------|----------------|-------|
| RTX 3060 | 12 GB | $220-300 | Best budget pick for AI |
| RTX 3060 Ti | 8 GB | $180-250 | Less VRAM — avoid for AI |
| RTX 3070 | 8 GB | $250-330 | Fast but only 8 GB |
| RTX 3080 | 10 GB | $320-420 | Powerful but 10 GB limits AI |
| RTX 3080 Ti | 12 GB | $450-580 | Good if budget allows |
| **RTX 3090** | **24 GB** | **$550-750** | **Best used option for serious AI** |
| RTX 4070 | 12 GB | $450-550 | Newer, efficient |

> **Best picks:** RTX 3060 12GB (budget) or RTX 3090 24GB (serious).
> Avoid all 8 GB cards — you hit the VRAM wall fast with AI.

---

## New vs Used — What to Buy Where

| Component | New or Used? | Reason |
|-----------|-------------|--------|
| GPU | **Used is fine** | RTX 3090 used = massive savings. Test before buying. |
| CPU | Either | Used CPUs rarely fail. Good savings. |
| RAM | Either | Used RAM is safe. |
| SSD | **New preferred** | Used SSDs have worn cells. Not worth the risk. |
| PSU | **New only** | Old or cheap PSUs can kill your whole build. Never used. |
| Motherboard | Either | Used fine from reputable seller. |

---

## California Tax Note

San Diego sales tax is ~8.75%.
Apply this to every in-store and most online purchases.
Factor it into your budget before you shop.

---

## How to Not Get Scammed on a GPU

### Red Flags — Walk Away

| Red Flag | Why |
|----------|-----|
| Price way below market (RTX 3090 for $200) | Scam or broken |
| Seller won't meet in person | Can't test it |
| Only stock photos, no real photos of the card | May not own it |
| "Moving away" or other sad story | Classic scam |
| Won't let you test before paying | Hiding a defect |
| Wants Zelle, Cash App, or wire transfer | No buyer protection |
| "Sold as-is" with no explanation | Hiding damage |
| Used for crypto mining (they admit it) | Mining destroys fans, VRAM, capacitors |

### Green Flags — Good Signs

| Green Flag | Why |
|------------|-----|
| Multiple real photos from different angles | They actually own it |
| Willing to meet in public | Legitimate |
| Will let you test in their PC | Best case |
| Has original box | Cared for it |
| Selling because they upgraded | Normal reason |
| Good FB Marketplace profile history | Proven seller |

---

## Where to Meet in San Diego

Always meet in a **public place with power** so you can test the GPU.

- **San Diego Police Department Safe Exchange Zones** — multiple SDPD stations have designated safe exchange zones for Craigslist/FB Marketplace meetups. Scammers almost never agree to meet at a police station. Search "SDPD safe exchange zone" for locations.
- **Best Buy** — park outside. Power available. Staff nearby.
- **Starbucks or coffee shop** — public, power outlets, cameras
- **Public library** — safe, has power

---

## How to Test a GPU Before Paying

### Visual Check
```
[ ] Fans spin freely when turned manually
[ ] No bent pins on connectors
[ ] No burn marks on the PCB (green board)
[ ] No cracked components
[ ] All ports (HDMI, DisplayPort) look clean and undamaged
```

### Software Check (Linux)
```bash
# GPU detected correctly
lspci | grep -i nvidia

# Check VRAM, temp, and driver
nvidia-smi
# Look for:
# - Correct GPU name (e.g. NVIDIA GeForce RTX 3090)
# - 24576 MiB VRAM for RTX 3090
# - Temp at idle: 30-50°C is normal. 80°C+ at idle = bad.
```

### Stress Test (5-10 Minutes)
```bash
# Install gpu_burn
git clone https://github.com/wilicc/gpu-burn
cd gpu-burn
make
./gpu_burn 300

# Any errors = VRAM damage = walk away
```

While running, GPU temp should stay under 85°C.
No screen artifacts. No crashes.

---

## How to Pay

| Method | Safe? | Notes |
|--------|-------|-------|
| **Cash** | Yes | Best for in-person. Count it in front of them. |
| **PayPal Goods & Services** | Yes | Has buyer protection. Worth the small fee. |
| Zelle | No | No protection. Gone if scammed. |
| Cash App | No | No protection. |
| Crypto | No | Never for parts. No recourse. |

---

## Workstation PC Deals in San Diego

Search Craigslist SD for old business workstations — they are underpriced:

| Model | Search | Expected Price | Notes |
|-------|--------|---------------|-------|
| HP Z440 | "HP Z440" | $150-300 | Xeon CPU, tons of RAM slots, add a GPU |
| Dell Precision T5810 | "Dell Precision T5810" | $150-300 | Workstation grade, easy upgrade |
| Lenovo ThinkStation P410 | "ThinkStation P410" | $200-400 | Reliable, good airflow |

Add a used RTX 3060 12GB (~$260) and total cost is under $550 for a solid AI machine.

---

## Recommended Shopping Strategy

```
Step 1: Check FB Marketplace SD for RTX 3090 ($650 max) or RTX 3060 12GB ($280 max)
        Watch for 1 week to learn market prices before buying

Step 2: Drive to Micro Center Tustin for CPU + Motherboard combo
        Buy cooler there too while you're at it

Step 3: Order RAM, SSD, PSU, Case from Amazon

Step 4: For coffee shop machine — Craigslist SD
        Search "Dell OptiPlex 7080 Tower" — budget $150-200
```
