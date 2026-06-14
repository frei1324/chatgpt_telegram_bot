<div align="center">

<img src="https://raw.githubusercontent.com/karfly/chatgpt_telegram_bot/main/static/header.png" align="center" style="width: 100%" />

# 🤖 ChatGPT Telegram Bot

**ChatGPT, re-created as a Telegram bot — and it works great.**

GPT-5.5 · Anthropic Claude (Opus / Sonnet / Haiku) · Vision · Voice · Image generation
<br/>Fast replies, no daily limits, message streaming and 15 special chat modes.

<p align="center">
<a href="https://t.me/jadvebot?start=source=github" alt="Run Telegram Bot"><img src="https://img.shields.io/badge/RUN-Telegram%20Bot-blue?logo=telegram" /></a>
<img src="https://img.shields.io/badge/python-3.12-blue?logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/docker-ready-2496ED?logo=docker&logoColor=white" />
<img src="https://img.shields.io/badge/license-MIT-green" />
<img src="https://img.shields.io/badge/version-1.3.0-orange" />
</p>

<p align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExYmM2ZWVjY2M4NWQ3ZThkYmQ3MDhmMTEzZGUwOGFmOThlMDIzZGM4YiZjdD1n/unx907h7GSiLAugzVX/giphy.gif" width="600" />
</p>

</div>

---

Web chatbots are great — but they're often laggy, rate-limited, and locked behind a browser tab. This project puts the best models from **OpenAI and Anthropic** **right inside Telegram**, with your own API keys and no daily limits.

🚀 **Try the live bot:** [@jadvebot](https://t.me/jadvebot) · 🌐 Web: [jadve.com](https://jadve.com) — or deploy your own in two commands ([Quick start ↓](#-quick-start)).

## ✨ Features

- ⚡ **Low latency** — replies usually take 3–5 seconds.
- 🔁 **No request limits** — you pay your API provider directly, nothing in between.
- 📝 **Message streaming** — answers stream into Telegram word-by-word.
- 🧠 **Frontier models** — **GPT-5.5** and **Anthropic Claude** (Opus 4.8 / Sonnet / Haiku) via [OpenRouter](https://openrouter.ai/), plus fast & cheap defaults out of the box.
- 👁️ **Vision** — send an image and any vision-capable model (GPT-5.5, Claude, …) will read it.
- 🎨 **Image generation** — create images with OpenAI `gpt-image-1` (switch to 👩‍🎨 *Artist* mode).
- 🎤 **Voice messages** — record a voice note and Whisper transcribes it for you.
- 🎭 **15 chat modes** — Assistant, Code Assistant, Psychologist, Elon Musk and more. Add your own in `config/chat_modes.yml`.
- 👥 **Group chat support** — run `/help_group_chat` for setup instructions.
- 💻 **Code highlighting** — formatted, readable code blocks.
- 🔒 **Access control** — restrict the bot to a list of allowed Telegram users.
- 💰 **Balance tracking** — see exactly how much you've spent on the API with `/balance`.

## 🧠 Supported models

Models are config-driven — add or remove any in [`config/models.yml`](config/models.yml) with **no code changes**.

| Model | Provider | Vision | Smart | Fast | Cheap | In / Out per 1K tokens |
|---|---|:---:|:---:|:---:|:---:|---|
| **GPT-4o mini** *(default)* | OpenAI | ✅ | 🟢🟢🟢🟢 | 🟢🟢🟢🟢🟢 | 🟢🟢🟢🟢🟢 | $0.00015 / $0.0006 |
| **GPT-4o** | OpenAI | ✅ | 🟢🟢🟢🟢🟢 | 🟢🟢🟢🟢 | 🟢🟢🟢🟢 | $0.0025 / $0.01 |
| **GPT-5.5** | OpenRouter | ✅ | 🟢🟢🟢🟢🟢 | 🟢🟢🟢 | 🟢🟢 | $0.005 / $0.03 |
| **Claude Opus 4.8** | OpenRouter | ✅ | 🟢🟢🟢🟢🟢 | 🟢🟢 | 🟢🟢 | $0.005 / $0.025 |
| **Claude Sonnet** | OpenRouter | ✅ | 🟢🟢🟢🟢🟢 | 🟢🟢🟢🟢 | 🟢🟢🟢 | $0.003 / $0.015 |
| **Claude Haiku** | OpenRouter | ✅ | 🟢🟢🟢🟢 | 🟢🟢🟢🟢🟢 | 🟢🟢🟢🟢 | $0.001 / $0.005 |

Plus `gpt-image-1` for image generation and **Whisper** for voice transcription.

> 💡 OpenAI models use the native API. Claude and GPT-5.5 are routed through [OpenRouter](https://openrouter.ai/) — just set `openrouter_api_key` and pick the model in `/settings`. Any other OpenRouter-routed model works too: declare `provider: openrouter` in `config/models.yml`.

## 🎭 Chat modes

| | | |
|---|---|---|
| 👩🏼‍🎓 General Assistant | 👩🏼‍💻 Code Assistant | 👩‍🎨 Artist |
| 🇬🇧 English Tutor | 💡 Startup Idea Generator | 📝 Text Improver |
| 🧠 Psychologist | 🚀 Elon Musk | 🌟 Motivator |
| 💰 Money Maker | 📊 SQL Assistant | 🧳 Travel Guide |
| 🥒 Rick Sanchez | 🧮 Accountant | 🎬 Movie Expert |

Create your own by editing [`config/chat_modes.yml`](config/chat_modes.yml).

## 🚀 Quick start

**1.** Get an [OpenAI API key](https://openai.com/api/).

**2.** *(optional)* Get an [OpenRouter API key](https://openrouter.ai/keys) to use **Claude** and **GPT-5.5**.

**3.** Get a Telegram bot token from [@BotFather](https://t.me/BotFather).

**4.** Fill in your tokens and rename the config files:

```bash
mv config/config.example.yml config/config.yml
mv config/config.example.env config/config.env
# then edit config/config.yml — set telegram_token, openai_api_key (and openrouter_api_key for Claude/GPT-5.5)
```

**5.** 🔥 Run it:

```bash
docker-compose --env-file config/config.env up --build
```

That's it — message your bot on Telegram.

## ⚙️ Configuration

Main options in `config/config.yml`:

| Option | Description |
|---|---|
| `telegram_token` | Bot token from [@BotFather](https://t.me/BotFather) |
| `openai_api_key` | Your OpenAI API key |
| `openai_api_base` | Custom base URL (e.g. [LocalAI](https://github.com/go-skynet/LocalAI)); leave `null` for default |
| `openrouter_api_key` | Needed only for `provider: openrouter` models (Claude, GPT-5.5) |
| `allowed_telegram_usernames` | Whitelist of users/IDs; empty = open to everyone |
| `new_dialog_timeout` | Seconds before a new dialog starts automatically |
| `image_size` | `gpt-image-1` output size (`1024x1024`, `1536x1024`, `1024x1536`, `auto`) |
| `enable_message_streaming` | Stream answers word-by-word |

Per-model pricing and capabilities live in [`config/models.yml`](config/models.yml).

## 💬 Bot commands

| Command | Description |
|---|---|
| `/new` | Start a new dialog |
| `/mode` | Select a chat mode |
| `/retry` | Regenerate the last answer |
| `/settings` | Choose model and settings |
| `/balance` | Show $ spent on the API |
| `/help` | Show help |

## 🗂️ Project structure

```
bot/
  bot.py           # Telegram handlers, streaming, commands
  openai_utils.py  # model dispatch (OpenAI + OpenRouter), token counting, vision
  config.py        # loads config.yml / models.yml / chat_modes.yml
  database.py      # MongoDB storage for users & dialogs
config/
  config.yml       # your tokens & settings
  models.yml       # model catalog, pricing, capabilities
  chat_modes.yml   # chat-mode prompts
```



