# AI Engines — Complete Setup Guide

One config file controls everything. Add a key, pick a model, assign per agent. Done.

---

## Quick start

```env
# .env — add only the providers you want to use

# ── ANTHROPIC (Claude) ──────────────────────────────
ANTHROPIC_API_KEY=sk-ant-...

# ── OPENAI ──────────────────────────────────────────
OPENAI_API_KEY=sk-...

# ── GOOGLE (Gemini + Veo3 + Imagen) ─────────────────
GOOGLE_API_KEY=AIza...

# ── KIMI / MOONSHOT (cheapest long-context) ─────────
MOONSHOT_API_KEY=sk-...

# ── LOCAL OLLAMA (no key needed) ────────────────────
OLLAMA_HOST=http://localhost:11434
# Models auto-detected from your Ollama install

# ── DEEPSEEK ────────────────────────────────────────
DEEPSEEK_API_KEY=sk-...

# ── GROQ (fastest inference) ────────────────────────
GROQ_API_KEY=gsk_...

# ── MISTRAL ─────────────────────────────────────────
MISTRAL_API_KEY=...

# ── XAI (Grok) ──────────────────────────────────────
XAI_API_KEY=xai-...

# ── DEFAULT MODEL (used when no override set) ────────
MODEL=anthropic/claude-sonnet-4-6
```

---

## Providers

### Claude — Anthropic
**Best for:** Reasoning, writing, coaching, long context  
**Price:** ~$3–15/M tokens  
**Signup:** [console.anthropic.com](https://console.anthropic.com)

```env
ANTHROPIC_API_KEY=sk-ant-api03-...
```

| Model | Context | Speed | Use case |
|---|---|---|---|
| `claude-sonnet-4-6` | 200K | Fast | Default — best balance |
| `claude-opus-4-5` | 200K | Slower | Complex reasoning, coaching |
| `claude-haiku-4-5` | 200K | Fastest | High-volume, quick tasks |

---

### OpenAI — GPT + Whisper + DALL-E
**Best for:** Code, structured output, image generation, transcription  
**Price:** ~$2.50–15/M tokens  
**Signup:** [platform.openai.com](https://platform.openai.com)

```env
OPENAI_API_KEY=sk-proj-...
```

| Model | Context | Use case |
|---|---|---|
| `gpt-4o` | 128K | Code, structured JSON, vision |
| `o1` | 200K | Deep reasoning tasks |
| `o3-mini` | 200K | Fast reasoning, low cost |
| `gpt-4o-mini` | 128K | High-volume, cheap |
| `whisper-1` | Audio | Speech-to-text (used by VOICE) |
| `dall-e-3` | — | Image generation |
| `tts-1-hd` | — | Text-to-speech |

---

### Google — Gemini + Veo 3 + Imagen
**Best for:** Multimodal, long video, fast inference, image generation  
**Price:** Gemini Flash ~$0.075/M tokens (cheapest multimodal)  
**Signup:** [aistudio.google.com](https://aistudio.google.com)

```env
GOOGLE_API_KEY=AIzaSy...
```

| Model | Context | Use case |
|---|---|---|
| `gemini-2.0-flash` | 1M | Fast, multimodal, cheapest |
| `gemini-1.5-pro` | 2M | Largest context window |
| `gemini-2.5-pro` | 1M | Best reasoning |
| `veo-3` | Video | Text-to-video generation |
| `imagen-3` | — | Text-to-image (photorealistic) |

**Veo 3 — text to video:**
```env
VEO3_MODEL=veo-3
VEO3_DURATION=8          # seconds
VEO3_RESOLUTION=1080p
VEO3_ASPECT_RATIO=16:9
```

---

### Kimi — Moonshot AI (cheapest long-context)
**Best for:** Long document analysis, cost-sensitive tasks, 128K context at near-zero cost  
**Price:** ~$0.12–0.50/M tokens — one of the cheapest available  
**Signup:** [platform.moonshot.cn](https://platform.moonshot.cn) or [kimi.ai](https://kimi.ai)

```env
MOONSHOT_API_KEY=sk-...
MOONSHOT_BASE_URL=https://api.moonshot.cn/v1
```

| Model | Context | Price/1M | Use case |
|---|---|---|---|
| `moonshot-v1-8k` | 8K | ~$0.12 | Fast, cheap |
| `moonshot-v1-32k` | 32K | ~$0.24 | Medium docs |
| `moonshot-v1-128k` | 128K | ~$0.50 | Entire codebases |

**Assign Kimi to cost-sensitive agents:**
```env
RADAR_MODEL=moonshot/moonshot-v1-128k   # 24/7 monitoring — save $$$
FORGE_MODEL=moonshot/moonshot-v1-32k    # Lead enrichment — high volume
```

---

### Ollama — Local (no API key)
**Best for:** Privacy, zero API cost, offline operation, experimentation  
**Price:** Free (compute is yours)  
**Install:** [ollama.com](https://ollama.com)

```bash
# Install
brew install ollama      # macOS
curl -fsSL https://ollama.com/install.sh | sh   # Linux

# Pull models
ollama pull llama3.2          # 3B — fast, lightweight
ollama pull llama3.3:70b      # 70B — best open-source quality
ollama pull mistral           # 7B — fast reasoning
ollama pull qwen2.5:72b       # 72B — strong multilingual
ollama pull deepseek-r1:7b    # 7B — reasoning, cheap
ollama pull codellama:34b     # 34B — code specialist
ollama pull phi4              # 14B — Microsoft, efficient
```

```env
OLLAMA_HOST=http://localhost:11434
# No key needed. Models auto-detected from your Ollama install.
```

Kapaciti auto-discovers all models you have pulled. List them:
```bash
ollama list
```

**Assign local models to privacy-sensitive agents:**
```env
COACH_MODEL=ollama/llama3.3:70b      # Client data — stays local
BUILD_MODEL=ollama/codellama:34b     # Code — stays local
```

---

### DeepSeek
**Best for:** Reasoning tasks, math, code — frontier quality at open-source prices  
**Price:** ~$0.14/M tokens (R1) — 95% cheaper than GPT-4o  
**Signup:** [platform.deepseek.com](https://platform.deepseek.com)

```env
DEEPSEEK_API_KEY=sk-...
```

| Model | Use case |
|---|---|
| `deepseek-r1` | Reasoning, analysis, complex tasks |
| `deepseek-v3` | General purpose, very fast |
| `deepseek-coder-v2` | Code generation and review |

---

### Groq — Fastest inference
**Best for:** Real-time tasks, sub-50ms responses, high-frequency agents  
**Price:** ~$0.27/M tokens for Llama 3.3 70B  
**Signup:** [console.groq.com](https://console.groq.com)

```env
GROQ_API_KEY=gsk_...
```

| Model | Speed | Use case |
|---|---|---|
| `llama-3.3-70b-versatile` | ~50ms | Best quality/speed ratio |
| `llama-3.1-8b-instant` | ~20ms | Ultra-fast, lightweight tasks |
| `mixtral-8x7b-32768` | ~30ms | Longer context, fast |
| `gemma2-9b-it` | ~25ms | Efficient, Google architecture |

**Assign Groq to time-sensitive agents:**
```env
RADAR_MODEL=groq/llama-3.3-70b-versatile   # Signal detection — needs speed
NEXUS_MODEL=groq/llama-3.1-8b-instant      # Routing — sub-50ms
```

---

### Mistral — Privacy-first European models
**Best for:** GDPR compliance, European data residency, efficient inference  
**Price:** ~$0.25–2/M tokens  
**Signup:** [console.mistral.ai](https://console.mistral.ai)

```env
MISTRAL_API_KEY=...
```

| Model | Context | Use case |
|---|---|---|
| `mistral-large-latest` | 128K | Complex reasoning |
| `mistral-small-latest` | 128K | Fast, low-cost |
| `mistral-nemo` | 128K | Lightweight, efficient |
| `codestral-latest` | 32K | Code completion |

---

### Grok — xAI (real-time X data)
**Best for:** Real-time X/Twitter data, current events, trend detection  
**Price:** ~$5–15/M tokens  
**Signup:** [console.x.ai](https://console.x.ai)

```env
XAI_API_KEY=xai-...
```

| Model | Use case |
|---|---|
| `grok-3` | Latest, most capable |
| `grok-2` | Stable, production |
| `grok-3-mini` | Fast, cost-efficient |

**Assign Grok to social agents:**
```env
RADAR_MODEL=xai/grok-3          # Real-time X signal detection
REACH_MODEL=xai/grok-3-mini     # Content that trends on X
```

---

### nano-banana — Vision & Image Processing
**Best for:** Image analysis, screenshot reading, OCR, visual workflows  
**Skill:** `nano-banana-pro` (included)

```env
# Uses your configured vision-capable model
VISION_MODEL=anthropic/claude-sonnet-4-6   # Default (best vision)
# Or:
VISION_MODEL=openai/gpt-4o                 # Alternative
VISION_MODEL=google/gemini-2.0-flash       # Fastest + cheapest vision
```

Capabilities:
- Read screenshots and extract data
- Analyze charts and trading setups
- Process documents and invoices
- OCR on any image format
- Compare before/after screenshots for testing

---

## Per-project model switching

Each project (or agent) can use a different model. Override in `.env`:

```env
# Global default
MODEL=anthropic/claude-sonnet-4-6

# Per-agent overrides
NEXUS_MODEL=groq/llama-3.1-8b-instant       # Routing — speed
PULSE_MODEL=anthropic/claude-sonnet-4-6     # Market intel — quality
COACH_MODEL=anthropic/claude-opus-4-5       # Coaching — best reasoning
FORGE_MODEL=moonshot/moonshot-v1-128k       # Pipeline — cheap, long context
CRAFT_MODEL=anthropic/claude-sonnet-4-6     # Content — quality
BUILD_MODEL=openai/gpt-4o                   # Code — GPT best for code
REACH_MODEL=anthropic/claude-haiku-4-5      # Social — high volume, fast
RADAR_MODEL=groq/llama-3.3-70b-versatile    # Signals — speed
VOICE_MODEL=anthropic/claude-opus-4-5       # Copy — best writing quality

# Per-project overrides (multi-project setup)
PROJECT_TRADING_MODEL=ollama/llama3.3:70b   # Trading project — local
PROJECT_SAAS_MODEL=deepseek/deepseek-r1     # SaaS project — cheap
PROJECT_CONTENT_MODEL=google/gemini-2.0-flash  # Content — fast + vision
```

---

## Cost comparison

| Provider | Model | $/1M input | $/1M output | Best for |
|---|---|---|---|---|
| **Kimi** | moonshot-v1-128k | $0.50 | $1.50 | Cheapest long-context |
| **DeepSeek** | deepseek-r1 | $0.14 | $2.19 | Cheapest reasoning |
| **Groq** | llama-3.3-70b | $0.59 | $0.79 | Fastest inference |
| **Google** | gemini-2.0-flash | $0.075 | $0.30 | Cheapest multimodal |
| **Mistral** | mistral-small | $0.20 | $0.60 | Cheapest European |
| **OpenAI** | gpt-4o-mini | $0.15 | $0.60 | Cheapest OpenAI |
| **Anthropic** | claude-haiku | $0.80 | $4.00 | Fastest Claude |
| **Anthropic** | claude-sonnet | $3.00 | $15.00 | Default (best balance) |
| **Ollama** | any | $0 | $0 | Free forever (local) |

**Aggressive cost optimization:**
```env
# $5-15/month total for full agent fleet
NEXUS_MODEL=groq/llama-3.1-8b-instant          # $0.05/day
PULSE_MODEL=moonshot/moonshot-v1-32k            # $0.10/day
COACH_MODEL=ollama/llama3.3:70b                 # $0
FORGE_MODEL=moonshot/moonshot-v1-128k           # $0.20/day
CRAFT_MODEL=google/gemini-2.0-flash             # $0.05/day
BUILD_MODEL=deepseek/deepseek-coder-v2          # $0.10/day
REACH_MODEL=groq/llama-3.1-8b-instant          # $0.03/day
RADAR_MODEL=groq/llama-3.3-70b-versatile        # $0.15/day
VOICE_MODEL=anthropic/claude-haiku-4-5          # $0.30/day
```

---

## Video generation — Veo 3

```bash
# Generate video from text
agent: "Create a 10-second product demo video showing the command center dashboard"

# Config
VEO3_MODEL=veo-3
VEO3_DURATION=8
VEO3_RESOLUTION=1080p
```

Veo 3 requires Google Cloud project with Video API enabled.  
Setup: [cloud.google.com/vertex-ai/docs/generative-ai/video](https://cloud.google.com/vertex-ai/docs/generative-ai/video)

---

## OAuth / Authentication

All providers use API key authentication — no OAuth flow required.

1. Sign up at the provider
2. Generate an API key
3. Add to `.env`
4. Done

No redirect URIs. No callback URLs. No OAuth apps to configure.

The only exception is Google Workspace tools (Gmail, Calendar, Drive) which use OAuth 2.0 via the `gog` skill — but that's separate from the AI model authentication.
