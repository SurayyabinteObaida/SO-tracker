# Amanah — Daily Compass

Personal productivity and deen tracking app. Single-file PWA. No server. No account.

## What it does
- Daily anchor sequence — time-aware, pre-decided, zero decisions
- Deen reflection — max 50 words, attached to existing habit
- Weekly depth ratings across 6 areas — deen, research, deep work, physical, finance, current affairs
- LLM mentor — OpenAI-powered research and financial mirror
- AES-GCM 256-bit encryption on API key via passphrase

## Deploy to GitHub Pages

1. Create a new GitHub repository (can be private)
2. Upload all files: index.html, manifest.json, sw.js, icon-192.png, icon-512.png
3. Go to Settings → Pages → Source: main branch, root folder
4. GitHub gives you a URL like: https://yourusername.github.io/amanah
5. Open that URL on your phone
6. Safari (iOS): Share → Add to Home Screen
   Chrome (Android): Menu → Add to Home Screen

## First open
1. Enter your name
2. Set a passphrase — minimum 8 characters, something you will remember
3. Enter your OpenAI API key (starts with sk-)
4. Set this month's research goal — one specific, falsifiable sentence
5. Set this month's financial intention — one sentence with a number

## Icons
Generate two square PNG icons:
- icon-192.png (192×192)
- icon-512.png (512×512)

Use any simple design — the Arabic word أمانة on a white background works well.
Free tool: https://favicon.io

## Security
- Your API key is encrypted with AES-GCM 256-bit using PBKDF2 key derivation (200,000 iterations)
- The raw key exists in memory only during an active session
- localStorage contains only the encrypted blob — useless without your passphrase
- Set a usage limit on your OpenAI account: $5/month is more than enough

## Recovery
If you forget your passphrase:
- Go to Settings → Export encrypted key blob (copy it somewhere safe first)
- Settings → Clear all data
- Set up again with a new passphrase and re-enter your API key
- Your weekly and daily data is lost — only the API key needs re-entry

## File structure
```
amanah/
  index.html     ← entire app
  manifest.json  ← PWA config
  sw.js          ← offline support
  icon-192.png   ← home screen icon (add yourself)
  icon-512.png   ← home screen icon (add yourself)
  README.md      ← this file
```

## Stack
- Vanilla HTML/CSS/JS — no framework, no build step
- Web Crypto API — built into every modern browser
- localStorage — data never leaves the device
- OpenAI gpt-4o-mini — mentor calls only, ~6 per month
- GitHub Pages — free hosting

## Layers
- Layer 1 (current): Shell, encryption, daily view, weekly ratings, LLM mentor
- Layer 2 (next): Financial hard cap tracking, 48-hour purchase log
- Layer 3 (future): Monthly goal archive, pattern insights
