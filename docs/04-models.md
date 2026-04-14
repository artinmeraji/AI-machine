# AI Models — Which One for What

All models run locally via Ollama. No internet. No API key. No filters from providers.

---

## For Your Cybersecurity Machine

| Model | Size | Pull Command | Best For |
|-------|------|-------------|---------|
| `dolphin-mistral` | 7B | `ollama pull dolphin-mistral` | General security assistant, no built-in refusals |
| `nous-hermes2` | 10.7B | `ollama pull nous-hermes2` | Uncensored, strong reasoning, CVE analysis |
| `qwen2.5-coder:14b` | 14B | `ollama pull qwen2.5-coder:14b` | Best local coding model — exploit scripts, tools |
| `deepseek-coder-v2` | 16B | `ollama pull deepseek-coder-v2` | Complex code, automation, tool building |
| `llama3.1:8b` | 8B | `ollama pull llama3.1:8b` | General research, explanations, CVE breakdown |
| `wizardlm2` | 7B | `ollama pull wizardlm2` | Instruction-following, task execution |
| `mistral-nemo` | 12B | `ollama pull mistral-nemo` | Fast, long context, good for reading logs/files |

### Recommended Starter Set (Pull These First)
```bash
ollama pull dolphin-mistral    # security assistant
ollama pull qwen2.5-coder:14b  # coding and scripting
ollama pull llama3.1:8b        # general research
```

---

## For Uncle's Coffee Shop

| Model | Size | Pull Command | Best For |
|-------|------|-------------|---------|
| `phi3-mini` | 3.8B | `ollama pull phi3-mini` | Best choice — fast, smart, tiny footprint |
| `llama3.2:3b` | 3B | `ollama pull llama3.2:3b` | Lightweight alternative |
| `mistral:7b` | 7B | `ollama pull mistral` | Smarter responses if hardware allows |
| `gemma2:9b` | 9B | `ollama pull gemma2:9b` | Polished, professional tone |

### Recommended for Coffee Shop
```bash
ollama pull phi3-mini    # if PC has 8-16 GB RAM
ollama pull mistral      # if PC has 16+ GB RAM
```

---

## Model Size vs VRAM Needed

| Model Size | Min VRAM (GPU) | Min RAM (CPU only) |
|-----------|---------------|-------------------|
| 3B | 2 GB | 4 GB |
| 7B | 5 GB | 8 GB |
| 13B | 8 GB | 16 GB |
| 14B | 10 GB | 20 GB |
| 34B | 20 GB | 40 GB |
| 70B (Q4) | 24 GB | 48 GB |

> Q4 = 4-bit quantized (compressed). Smaller file, slightly less smart, fits in less VRAM.
> Your RTX 3090 (24 GB) runs 34B full or 70B Q4.

---

## Understanding Model Names

```
llama3.1:8b        →  Llama 3.1 model, 8 billion parameters
qwen2.5-coder:14b  →  Qwen 2.5 Coder, 14 billion parameters
mistral:7b-q4      →  Mistral 7B, 4-bit quantized (compressed)
dolphin-mistral    →  Dolphin fine-tune of Mistral (uncensored)
```

Numbers after the colon = billions of parameters.
More parameters = smarter but slower and needs more VRAM.

---

## What "Uncensored" Means

Standard models (like base Llama) have refusal training — they decline certain topics.
Uncensored fine-tunes (Dolphin, Nous-Hermes, WizardLM) have reduced or removed refusals.

For cybersecurity use, uncensored models are more useful because they:
- Explain how exploits work without lecturing
- Write security tools without refusing
- Discuss CVE details directly
- Help with CTF challenges without hedging

You can also override behavior on any model using a custom system prompt in a Modelfile.
See `docs/07-ollama-setup.md` for how to build custom models.

---

## Checking What's Downloaded

```bash
# List all models on your machine
ollama list

# Check storage used
du -sh ~/.ollama/models/

# Remove a model you don't need
ollama rm model-name
```

---

## Model Storage Location

Models are stored at:
```
~/.ollama/models/
```

Average model sizes:
- 7B model = ~4-5 GB
- 14B model = ~8-9 GB
- 34B model = ~20-22 GB
- 70B Q4 model = ~38-42 GB

With a 1 TB SSD: you can store ~8-10 large models or 15-20 small ones.
