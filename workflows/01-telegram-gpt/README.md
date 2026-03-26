# 01 — Telegram GPT Assistant

Simple AI assistant: receives messages via Telegram, processes them through OpenAI GPT-4o-mini, and replies back in the same chat.

First working n8n agent — foundation for more complex workflows.

---

## Architecture

```
Telegram (user message)
        ↓
  Telegram Trigger
        ↓
   OpenAI GPT-4o-mini
        ↓
  Telegram (send reply)
```

---

## Nodes

| Node | Role |
|---|---|
| Telegram Trigger | Receives incoming messages via webhook |
| OpenAI | Sends message to GPT-4o-mini, gets response |
| Telegram | Sends reply back to the user |

---

## Setup

### 1. Telegram Bot
1. Create a bot via [@BotFather](https://t.me/BotFather) → get token
2. In n8n: add **Telegram** credential with the bot token
3. Set webhook URL to your n8n instance (ngrok for local, domain for VPS)

### 2. OpenAI
1. Get API key from [platform.openai.com](https://platform.openai.com)
2. In n8n: add **OpenAI** credential with the API key

### 3. Import workflow
1. In n8n: **Workflows → Import from file** → select `workflow.json`
2. Update credentials on Telegram Trigger and OpenAI nodes
3. Activate the workflow

---

## Requirements

- n8n (self-hosted or cloud)
- Telegram Bot token
- OpenAI API key (GPT-4o-mini — cost-efficient, ~$0.15/1M tokens)
- Public URL for webhook (ngrok for dev, nginx + SSL for production)

---

## Stack

`n8n` · `Telegram Bot API` · `OpenAI API` · `GPT-4o-mini`
