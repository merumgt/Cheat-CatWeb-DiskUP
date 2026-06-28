# CatWeb Bot `v1.0.2`

A Discord bot that lets you scrape and inspect any **CatWeb** site directly from Discord.

> **Join the Discord to try it out:** [discord.gg/NFHVPuZx9](https://discord.gg/NFHVPuZx9)

---

## What it does

- `/scrap-site <url>` — Returns the full data of any CatWeb site as a JSON file
- `/info-site <url>` — Returns info about a site (creator, visits per min/hr/day/week, elements, creation date...)
- `/stalk <username or id>` — Returns all sites owned by a Roblox user with their visits, total combined visits, bio, join date

---

## How to get access

Access is protected by a key system. Keys are valid for **24 hours**.

1. Use any command in the server
2. Click **Get key** and complete the checkpoint
3. Click **Redeem token**, paste your token
4. You're in

---

## Commands

| Command | Description |
|---|---|
| `/scrap-site <url>` | Get the full data of a CatWeb site |
| `/info-site <url>` | Get info and visit stats about a CatWeb site |
| `/stalk <username\|id>` | Get all sites and total visits from a Roblox user |
| `/keyinfo` | Check how much time is left on your key |

---

## Changelog

### v1.0.2
- `/stalk` now fetches all sites in parallel batches — supports 100+ sites
- Visit rates on `/info-site` now calculated from site creation date
- Thumbnail displayed in `/info-site` embed
- Username support for `/stalk` (auto-resolves to Roblox ID)
- Server down message instead of generic timeout error

### v1.0.1
- Added `/stalk` command
- Added visit rates (per min / hr / day / week) on `/info-site`
- Fixed visit count parsing (`308K`, `1.2M` formats)
- Fixed timestamps display (Unix → readable date)

### v1.0.0
- Initial release
- `/scrap-site`, `/info-site`
- WorkInk key system with 24h access
- Fake memory log disguise
