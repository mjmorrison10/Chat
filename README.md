# Lust 💜

A private, mobile-first web app for chatting with uncensored AI characters. Single-page PWA, zero backend, no signup — just bring your own OpenRouter API key.

![Lust](icon-192.png)

## ✨ Features

- 🎭 **Unlimited custom characters** — name, avatar, description, personality, scenario, first message, system prompt
- 💾 **All data in browser localStorage** — characters + chat history persist across sessions
- 🧠 **Full in-session memory** — entire conversation is sent as context to the model
- 🔍 **Browse TavernAI community characters** — search 270K+ characters from Chub.ai
- 🔗 **Import from URL** — paste a link to any hosted character card
- 📁 **Import from file** — supports `.json` and TavernAI/SillyTavern V2/V3 PNG cards
- ⬆️ **Export individual or all characters** as portable JSON
- 🔄 **Regenerate** any response with one tap
- ⚙️ **Switch models** on the fly
- 📱 **Installable PWA** — adds to iPhone/Android home screen, launches fullscreen
- 🔒 **Private** — your API key never leaves your device except to OpenRouter

## 🚀 Quick Start

### 1. Get an OpenRouter API key (free)

1. Sign up at [openrouter.ai](https://openrouter.ai)
2. You get **$5 in free credits** automatically
3. Create a key at https://openrouter.ai/keys
4. Copy it (starts with `sk-or-v1-...`)

### 2. Run locally

```bash
cd lust
python3 -m http.server 8000
```

Then open http://localhost:8000 in your browser.

### 3. Or deploy to Vercel (free, 30 seconds)

```bash
npx vercel
```

You'll get a URL like `https://lust-xyz.vercel.app`. Open it on your phone → Add to Home Screen.

## 📱 Use It On Your Phone

After deploying or running on a server:

- **iPhone:** Open in Safari → Share button → "Add to Home Screen"
- **Android:** Open in Chrome → menu → "Install app"

It installs as a real app icon and launches fullscreen like a native app.

## 🛠️ How It Works

- Single-page PWA: `index.html` (HTML + CSS + JS in one file, ~55 KB)
- Calls OpenRouter's API directly from your browser (CORS is enabled there)
- Your API key + characters + chat history live in `localStorage` — never sent anywhere except OpenRouter
- PNG character cards (TavernAI / SillyTavern V2/V3 spec) are parsed in-browser by extracting JSON from PNG metadata `tEXt` chunks

## 🤖 Models

Pre-configured options in the dropdown (all uncensored):

| Model | Notes |
|---|---|
| **Euryale 2 70B** (default) | Gold standard for NSFW RP. Great prose, no refusals. |
| **Rocinante 12B** | Fast, smart, good for weak networks. |
| **Midnight Rose 70B** | Poetic, romantic. |
| **Lumimaid 70B** | Softer emotional tone. |
| **DeepSeek V3** | Cheapest option (~¢0.14 per 1M tokens). |
| **Dolphin Mistral 24B** | Reliable all-rounder. |
| **Qwen 2.5 72B** | Strong multilingual. |

## 💸 Cost

For one person chatting casually: **$2–10/month** depending on model.
The $5 free credit lasts ages on cheaper models.

## 📂 Files

```
lust/
├── index.html       # The entire app (HTML + CSS + JS in one file)
├── manifest.json    # PWA install config
├── sw.js            # Service worker (offline shell)
├── icon-192.png     # App icon (small)
├── icon-512.png     # App icon (large)
├── vercel.json      # Vercel deploy config
├── README.md        # You are here
└── .gitignore
```

## 🔒 Privacy

- No tracking
- No analytics
- No server-side storage
- API key + characters + chats live only in your browser's `localStorage`
- The only network requests are: (1) load static files, (2) call OpenRouter API, (3) optionally fetch Chub.ai search + character cards

## 📋 Character Card Compatibility

Imports/exports work with:
- **V2/V3 PNG cards** (TavernAI / SillyTavern standard) — parses embedded JSON from PNG metadata
- **Raw JSON files** in any of these shapes:
  - `{"characters": [...]}` — Lust's own export format
  - `{"character": {...}}` — wrapped single
  - `{name, ...}` — raw single character
  - `[{...}, {...}]` — bare array

## 🌐 Browse Community Characters

The app searches Chub.ai directly (the active character-card database that TavernAI / SillyTavern users rely on). You can:
- Search by name/keyword
- Filter NSFW / SFW
- Sort by stars or newest
- One-tap import any character (downloads the PNG card, parses it, saves locally)

## ⚖️ License

Do whatever you want. This is your code.
