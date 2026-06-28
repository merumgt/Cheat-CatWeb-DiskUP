# CatWeb Bot

A Discord bot that lets you scrape and inspect any **CatWeb** site (Roblox browser game) directly from Discord.

> **Try it out — join the Discord server:** [discord.gg/INVITE](https://discord.gg/INVITE)

---

## Features

- `/scrap-site <url>` — Returns the full JSON of any CatWeb site
- `/info-site <url>` — Returns metadata (creator, visits, elements, pages...)
- Key system powered by **WorkInk** — get 24h access by completing a checkpoint
- Admin commands to grant/revoke access manually

---

## How to get access

1. Use `/scrap-site` or `/info-site` in the Discord server
2. Click **Get key** — complete the WorkInk checkpoint
3. Click **Redeem token** and paste your token
4. Done — access is valid for **24 hours**, then you need a new key

---

## Commands

| Command | Description |
|---|---|
| `/scrap-site <url>` | Get the full JSON of a CatWeb site |
| `/info-site <url>` | Get metadata about a CatWeb site |
| `/getkey` | Get the WorkInk link to obtain a key |
| `/redeem <token>` | Activate a WorkInk token manually |
| `/keyinfo` | Check how much time is left on your key |

---

## Self-hosting

### Requirements

```
Python 3.11+
discord.py >= 2.3.0
aiohttp >= 3.9.0
ngrok (or any public tunnel / VPS)
```

### Setup

```bash
git clone https://github.com/YOU/catweb-bot
cd catweb-bot
pip install -r requirements.txt
```

Edit `bot.py` and fill in:

```python
TOKEN       = "your Discord bot token"
ADMIN_IDS   = {your Discord user ID}
GETKEY_LINK = "your WorkInk link"
```

Start ngrok in one terminal:
```bash
ngrok http 8765
```

Start the bot in another:
```bash
python bot.py
```

### WorkInk setup

1. Go to [work.ink](https://work.ink) → Integrations → Key System → API
2. Click **Generate Link** — use `https://work.ink/token` as the destination
3. Paste the generated link into `GETKEY_LINK` in `bot.py`

---

## How it works

The bot runs an HTTP server locally (port 8765). A Lua script running inside Roblox (via an executor) polls the server for jobs, executes `dns_lookup` on the target URL, and posts the result back. The bot then sends it to Discord.

```
Discord user                Bot (Python)              Roblox executor (Lua)
     │                          │                              │
     │  /scrap-site google.rbx  │                              │
     │─────────────────────────>│                              │
     │                          │── POST job to queue ────────>│
     │                          │                              │ dns_lookup("google.rbx")
     │                          │<── POST result ─────────────│
     │<── JSON / file ──────────│                              │
```

---

## License

MIT
