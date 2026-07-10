# Workflows

This directory contains sanitized n8n workflows, organized by use case.

## Top-level layout

```
workflows/
├── featured/           # Two big workflows with their own repos (sanitized copies)
├── video/              # AI video generation, automated publishing
├── content-production/ # Long-form content (Volt, Alpha Girl)
├── voice-tts/          # Voice synthesis workflows
├── commerce/           # E-commerce, payments, orders
├── customer-support/   # AI customer support
├── ai-agents/          # RAG demos, AI agent frameworks
├── data-harvesting/    # Reddit scraping, content aggregation
├── email-processing/   # Gmail integrations
├── podcast/            # Podcast-to-content pipeline
├── ops/                # Error notifications, monitoring
├── experimental/       # Work-in-progress, sub-workflows
└── other/              # Miscellaneous
```

Each `.json` file is a complete, importable n8n workflow.

## How to import

```bash
# In n8n UI:
Workflows → Import from File → select a .json file
```

After import:
1. Open each node that uses credentials
2. Create the credential in n8n (Settings → Credentials)
3. Assign the credential to the node
4. Replace any `Bearer <TOKEN>` style placeholders with actual API keys

## Sanitization

All workflows have been sanitized:
- API keys → `<API_KEY>`, `<MINIMAX_KEY>`, etc.
- Bearer tokens → `<TOKEN>`
- Chat IDs → `<CHAT_ID>`

The structure, prompts, and logic are unchanged. Only secrets are redacted.

## License

MIT for all workflows in this directory.