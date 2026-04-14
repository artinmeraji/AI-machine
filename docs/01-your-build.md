# Your Build — Cybersecurity AI Machine

**Budget:** $1,200-1,500
**Location:** San Diego, California

---

## The Rule That Matters Most

> **The GPU is everything.**
> Local AI speed is determined almost entirely by GPU VRAM.
> More VRAM = bigger models = smarter AI = faster responses.
> Spend here before anywhere else.

---

## Your Exact Parts List

| Component | Exact Pick | Buy Where | Est. Price | Why |
|-----------|-----------|-----------|-----------|-----|
| **GPU** | RTX 3090 24GB (used) | FB Marketplace SD | $550-680 | 24 GB VRAM runs 34B models. The heart of this build. |
| **CPU** | AMD Ryzen 7 5700X | Micro Center Tustin | $149-169 | 8 cores, great for AI + security tools running together |
| **Motherboard** | MSI B550 Tomahawk | Micro Center Tustin | $129-149 | Buy with CPU for combo discount. PCIe 4.0. Reliable. |
| **RAM** | 32 GB DDR4 3200MHz G.Skill Ripjaws (2x16GB) | Amazon | $55-70 | Enough for model + OS + tools + browser simultaneously |
| **Storage** | 1 TB NVMe SSD — WD Black SN770 | Amazon | $65-80 | Fast. Holds OS + 5-6 large models comfortably. |
| **PSU** | Corsair RM850x 850W Gold | Amazon | $120-140 | RTX 3090 uses 350W alone. 850W gives safe headroom. |
| **Case** | Fractal Design Meshify C | Amazon | $85-95 | Excellent airflow. RTX 3090 runs hot. Easy build. |
| **CPU Cooler** | DeepCool AK400 | Amazon | $35-45 | Ryzen 7 gets hot under AI load. Stock cooler not enough. |
| **Total** | | | **$1,188-1,428** | |

---

## To Hit $1,200 vs $1,500

**Staying at $1,200:**
- Find RTX 3090 at $550 (be patient, check FB Marketplace daily)
- Use Micro Center CPU + Motherboard combo deal (saves $20-30)
- Lower end RAM kit (~$55)
- **Total: ~$1,190-1,250**

**Using up to $1,500:**
- Budget up to $680 for RTX 3090 (easier to find fast)
- Upgrade to 2 TB NVMe (~$110) for more model storage
- Add a 2 TB SATA SSD (~$100) dedicated to models
- **Total: ~$1,400-1,500**

---

## What This Machine Can Run

| Model | Size | Speed | Best For |
|-------|------|-------|----------|
| `dolphin-mistral` | 7B | 50-70 tok/sec | Fast security assistant, no filter |
| `qwen2.5-coder:14b` | 14B | 25-40 tok/sec | Code generation, exploit scripts |
| `nous-hermes2` | 34B | 8-15 tok/sec | Deep reasoning, complex analysis |
| `llama3.1:70b` (Q4 compressed) | 70B | 3-6 tok/sec | Near GPT-4 level, runs slow but works |

---

## GPU VRAM Quick Reference

| VRAM | What You Can Run |
|------|-----------------|
| 4 GB | 3B models only |
| 6 GB | 7B compressed |
| 8 GB | 7B comfortably |
| **12 GB** | **7B great, 13B comfortable** |
| 16 GB | 13B great, 34B compressed |
| **24 GB** | **34B great, 70B compressed — this build** |
| 48 GB+ | 70B great, research level |

---

## Why These Parts Were Chosen

**RTX 3090 over RTX 3080:**
The 3090 has 24 GB vs 3080's 10 GB. At 24 GB you run 34B models easily.
At 10 GB you're capped at 7B. $100-200 more used, 2-3x the capability.

**Ryzen 7 5700X over Intel i7:**
Cheaper, same AI performance, cooler, less power. AM4 = cheap motherboards.

**MSI B550 Tomahawk over budget boards:**
PCIe 4.0 for faster GPU bandwidth. Known reliability. Good VRM under load.

**850W PSU over 750W:**
RTX 3090 = 350W. Ryzen 7 = 65W. System peak = ~450W.
PSU at 50-60% load lasts longer and runs quieter than one at 90%.

**32 GB RAM over 64 GB:**
At this budget, GPU VRAM is more important than system RAM.
32 GB handles everything comfortably. Upgrade later for $50-70.

---

## Budget Starter Option (~$600-850)

If you want to start cheaper and upgrade the GPU later:

| Component | Pick | Price |
|-----------|------|-------|
| GPU | RTX 3060 12GB (used) | $240-300 |
| CPU | AMD Ryzen 5 5600 | $100-130 |
| Motherboard | MSI B550M PRO-VDH | $90-110 |
| RAM | 32 GB DDR4 3200MHz | $50-70 |
| Storage | 1 TB NVMe SSD | $70-90 |
| PSU | EVGA SuperNOVA 650W Gold | $80-100 |
| Case | Any mid-tower with mesh front | $50-70 |
| CPU Cooler | Cooler Master Hyper 212 | $30-40 |
| **Total** | | **~$710-910** |

**Upgrade path:** Same board, same CPU, same RAM. Swap RTX 3060 → RTX 3090 later.

---

## Shopping Order — Do This in This Order

```
Day 1-7:   Watch FB Marketplace San Diego daily
           Search: "RTX 3090"
           Max budget: $680
           Just watch — learn the market before buying

Day 1-3:   Drive to Micro Center Tustin (weekend trip)
           Buy: Ryzen 7 5700X + MSI B550 Tomahawk (ask for combo deal)
           Buy: DeepCool AK400 cooler while there

Day 1-3:   Order from Amazon
           → 32 GB DDR4 G.Skill Ripjaws (2x16GB)
           → WD Black SN770 1TB NVMe
           → Corsair RM850x 850W
           → Fractal Design Meshify C

Day 7-14:  Buy RTX 3090 when good deal appears
           → Follow buying checklist in docs/03-buying-guide.md
           → Test before paying
           → Negotiate $30-50 below asking price

Day 14-21: Build the machine
           → Follow docs/05-assembly.md
```
