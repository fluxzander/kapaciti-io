# Agent Fleet

Nine purpose-built agents. Each has a specialized prompt, specialized skills and specialized output. No generalist chatbots.

---

## NEXUS — Command Layer

**Model:** Claude Sonnet (default)  
**Schedule:** Always-on  
**Skills:** `agent-orchestrator`, `cognitive-memory`, `mcp-builder`

Routes every incoming task to the right specialist. Parses intent, enriches context, dispatches, consolidates results. The orchestration layer that makes the other eight agents work as a system.

---

## PULSE — Market Intelligence

**Model:** Claude Sonnet or GPT-4o  
**Schedule:** Mon–Fri 09:00  
**Skills:** `financial-data`, `blogwatcher`, `web_search`

Publishes a daily market briefing before trading opens. Sources: macro data, economic calendar, geopolitical feeds, Fear & Greed Index, oil, gold, BTC. Written in natural prose, no bullet points. Posted to the configured Discord channel automatically.

---

## COACH — Client Coaching Engine

**Model:** Claude Opus (default for quality)  
**Schedule:** On-message + daily 10:00 check  
**Skills:** `trading-journal`, `trading-coach`, `day-trading-investor-pro`

Reads client trade journals, identifies behavioral patterns (FOMO, revenge trading, oversizing, hope trading), drafts personalized coaching responses in your exact voice. Queues drafts for your approval — never sends autonomously.

---

## FORGE — Revenue & Pipeline

**Model:** DeepSeek R1 or Claude Sonnet  
**Schedule:** Mon–Fri 09:00  
**Skills:** `lead-hunter`, `firecrawl`, `kapaciti-sales`, `stripe`, `lead-generation`

Finds prospects via web scraping and social listening. Enriches with email, LinkedIn and company data. Runs multi-touch email sequences. Tracks responses. Escalates warm leads. Integrates with Stripe for invoice generation.

---

## CRAFT — Content Engine

**Model:** Claude Sonnet  
**Schedule:** Daily 09:00  
**Skills:** `mia-content-creator`, `content-repurposing`, `video-scripts`, `newsletter-creation-curation`, `typefully`

Takes any content input — tweet, voice memo, call transcript, article — and produces platform-adapted output: X threads, newsletter issues, TikTok scripts, email sequences. Schedules via Typefully.

---

## BUILD — Code & Infrastructure

**Model:** Claude Sonnet or GPT-4o  
**Schedule:** On-demand  
**Skills:** `coding-agent`, `supabase`, `notion`, `github`, `webapp-testing`, `playwright-automation`, `docker-deploy`, `api-builder`

Full-stack agent. Writes code, runs database migrations, manages GitHub PRs, deploys APIs, runs UI test suites, containerizes projects. Handles schema design through production deploy.

---

## REACH — Social Execution

**Model:** Claude Haiku (fast, high-volume)  
**Schedule:** Daily 09:00  
**Skills:** `x-automation`, `typefully`, `tiktok-scraping-yt-dlp`, `tiktok-viral-marketing`

Posts to TikTok, Instagram and X on schedule. Adapts copy per platform. Tracks engagement and adjusts cadence. Sources content from CRAFT's production queue.

---

## RADAR — Signal Detection

**Model:** Claude Haiku or Groq (speed)  
**Schedule:** Every 2h during market hours  
**Skills:** `web_search`, `blogwatcher`, `qmd`, `competitive-intelligence-market-research`

Monitors Reddit, X, TradingView, HackerNews, RSS feeds. Filters noise. Surfaces only high-signal events: competitor moves, unusual volume, viral mentions, macro surprises. Posts digest to configured channel.

---

## VOICE — Brand Copywriting

**Model:** Claude Opus  
**Schedule:** On-demand  
**Skills:** `landing-page-generator`, `newsletter-creation-curation`, `brand-voice`, `stop-slop`

Writes in your brand voice. Email sequences, ad copy, landing pages, sales scripts. Trained on your existing content. Runs the output through Stop-Slop to eliminate filler, passive voice and AI-sounding phrases.

---

## Configuration

Each agent can be assigned its own model in `.env`:

```env
NEXUS_MODEL=anthropic/claude-sonnet-4-6
PULSE_MODEL=openai/gpt-4o
COACH_MODEL=anthropic/claude-opus-4-5
FORGE_MODEL=deepseek/deepseek-r1
CRAFT_MODEL=anthropic/claude-sonnet-4-6
BUILD_MODEL=openai/gpt-4o
REACH_MODEL=anthropic/claude-haiku-4-5
RADAR_MODEL=groq/llama-3.3-70b
VOICE_MODEL=anthropic/claude-opus-4-5
```
