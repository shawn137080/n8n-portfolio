# n8n Portfolio

> A collection of production n8n workflows demonstrating automation patterns, AI integration, and content pipelines.

This repo is a **portfolio** — it shows what I (Shawn Pan) build with n8n in production. Two of the most complex workflows have dedicated repos; everything else lives here, organized by use case.

---

## Highlighted projects

These two workflows are large enough to warrant their own repositories:

| Project | Description | Repo |
|---------|-------------|------|
| **AI Video Pipeline** | 51-node workflow that produces a video and publishes it to TikTok, Instagram, YouTube, Facebook, LinkedIn daily | [n8n-ai-video-pipeline](https://github.com/shawn137080/n8n-ai-video-pipeline) |
| **Ask Uncle Sleep** | 31-node modular podcast script generator using chained LLM calls | [n8n-ask-uncle-sleep](https://github.com/shawn137080/n8n-ask-uncle-sleep) |

Sanitized copies are also included in [`workflows/featured/`](workflows/featured/) for visibility.

---

## Categories

| Category | Count | What it is |
|----------|-------|------------|
| [`video/`](workflows/video/) | 2 | AI video generation, automated publishing |
| [`content-production/`](workflows/content-production/) | 6 | Long-form content generation (Volt, Alpha Girl Revenge pipeline) |
| [`voice-tts/`](workflows/voice-tts/) | 4 | Voice synthesis, ElevenLabs, TTS pipelines |
| [`commerce/`](workflows/commerce/) | 8 | Order/payment matching, e-commerce automation |
| [`customer-support/`](workflows/customer-support/) | 2 | AI customer support agents |
| [`ai-agents/`](workflows/ai-agents/) | 2 | RAG demos, AI agent frameworks |
| [`data-harvesting/`](workflows/data-harvesting/) | 2 | Reddit scraping, content aggregation |
| [`email-processing/`](workflows/email-processing/) | 1 | Gmail integration, email-to-sheet |
| [`podcast/`](workflows/podcast/) | 1 | Podcast-to-content pipeline (Open Notebook engine) |
| [`ops/`](workflows/ops/) | 2 | Error notifications, monitoring |
| [`experimental/`](workflows/experimental/) | 9 | Work-in-progress, sub-workflows |
| [`other/`](workflows/other/) | 2 | Miscellaneous |

**Total: 42 workflows**

---

## What these workflows demonstrate

### Patterns I use repeatedly

- **Webhook → API → Notification** — receive a request, transform, notify. The basic building block.
- **Schedule → Multi-stage AI → Multi-platform publish** — content creation at scale.
- **Gmail/Sheet → AI agent → Telegram/Slack** — human-in-the-loop automation.
- **Code nodes for transforms** — when you need a 5-line JavaScript, don't reach for an LLM.
- **Modular sub-workflows** — break monolithic workflows into callable units.

### Tools I integrate with

| Tool | Used in | Purpose |
|------|---------|---------|
| OpenAI | Most workflows | LLM, embeddings, DALL-E, TTS |
| Anthropic Claude | A few | Alternative LLM |
| Google Gemini | Several | Alternative LLM, free tier |
| OpenRouter | Several | LLM routing |
| Deepgram | Podcast | STT with diarization |
| ElevenLabs | Voice workflows | High-quality TTS |
| Discord | Many | Notifications |
| Telegram | Many | Notifications, bot commands |
| Google Sheets | Many | State store, queue |
| Google Drive | Video | File archival |
| Reddit API | Data harvesting | Content scraping |
| Open Notebook | Podcast | RAG + content engine |

---

## About the workflows

These are **production workflows** — they run in real environments, not throwaway demos. They were extracted from a self-hosted n8n instance (local Docker + VPS) and sanitized before publishing.

### Sanitization

All workflows have been sanitized:
- API keys replaced with `<API_KEY>`, `<MINIMAX_KEY>`, etc.
- Bearer tokens replaced with `<TOKEN>`
- Specific chat IDs / channel IDs replaced with `<CHAT_ID>`

To use them, configure credentials in the n8n UI after import.

### How to import a workflow

```bash
# In n8n UI
Workflows → Import from File → select any *.json file
```

Then assign credentials to each node that needs one.

---

## Selected workflow highlights

### Volt (18 nodes)
Long-form content pipeline: Google Sheets input → OpenAI script generation → multi-stage transforms → publish to multiple platforms. Demonstrates parallel branching and complex state management.

### Reddit Story Harvester (18 nodes)
Cron-triggered scraper that pulls top Reddit stories, summarizes them with Gemini, and posts to a queue. Demonstrates data harvesting + AI summarization + queue management.

### AI Video Pipeline (51 nodes)
The biggest one. Daily-triggered pipeline that produces and publishes a fully edited video to 5 social platforms. See [n8n-ai-video-pipeline](https://github.com/shawn137080/n8n-ai-video-pipeline) for full details.

### Customer Support Agents (2 workflows)
AI agents that handle tier-1 customer support queries for an e-commerce store. RAG over product docs, with escalation to humans when confidence is low.

### Commerce Pipeline (8 workflows)
NP — a real production e-commerce automation:
- Order email → Google Sheet
- Interac payment → Telegram alert
- Order + payment matching
- Daily cleanup
- And 4 more

This is real money moving through real systems.

---

## Working with these

### To run a workflow locally

```bash
# Clone
git clone https://github.com/shawn137080/n8n-portfolio
cd n8n-portfolio

# Start n8n
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

Open http://localhost:5678 and import any workflow from `workflows/`.

### To see it in production

Most of these run on:
- A self-hosted n8n instance (Docker on Mac)
- A small VPS for always-on automations (Reddit scraping, daily video generation)

---

## What I look for in a new workflow

1. **It solves a real problem** — not a contrived demo.
2. **It's modular** — each stage can be edited without rewriting the whole thing.
3. **It handles failure** — retries, timeouts, fallbacks.
4. **It's transparent** — sticky notes document each stage.
5. **It's measurable** — token usage, execution time, success rate are all logged.

---

## Contact

Built by [Shawn Pan](https://github.com/shawn137080).
Singapore-based. Available for automation consulting.

---

## License

MIT.