# UGC Studio — AI Lifestyle Shot Generator

Generate realistic UGC and lifestyle shots from any product URL. Paste a product link, the tool scrapes product images and brand info, then uses Gemini AI to produce authentic-looking user-generated content photos.

## What It Does

1. **Scrapes** the product page (product name, brand, target audience, images) using Gemini URL context or CORS proxy fallback
2. **Fetches** the product image as a visual reference for the AI
3. **Generates** UGC-style prompts tailored to the brand and audience
4. **Creates** lifestyle images featuring the actual product — 6 shot types available

**Shot Types:** Authentic Hold · Lifestyle Scene · Unboxing · Social Setting · Outdoor/Active · Detail Close-Up

---

## Setup — GitHub Pages

1. Create a new repo (e.g. `ugc-studio`) under your GitHub org
2. Push this code to the `main` branch
3. Go to **Settings → Pages → Source → Deploy from branch → main / (root)**
4. Wait ~60 seconds, then visit `https://your-org.github.io/ugc-studio`

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR-ORG/ugc-studio.git
git push -u origin main
```

---

## Notion Embed

Once GitHub Pages is live (must be HTTPS):

1. In Notion, type `/embed`
2. Paste your GitHub Pages URL: `https://your-org.github.io/ugc-studio`
3. Resize the embed block to fill the page width

> GitHub Pages provides HTTPS automatically — required for Notion embeds.

---

## API Key

- Get a free Gemini API key at [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
- Enter it on first load — stored in `localStorage`, never sent to any server
- Use the settings gear (top right) to update the key at any time

---

## Image Generation Model

The Gemini image generation model name changes periodically. The current model is set in `index.html`:

```javascript
IMAGE_MODEL: 'gemini-3-pro-image-preview',
```

If image generation fails with a model-not-found error, check the latest model name at:
[ai.google.dev/gemini-api/docs/image-generation](https://ai.google.dev/gemini-api/docs/image-generation)

---

## File Structure

```
ugc-studio/
├── index.html          # Everything — all HTML, CSS, JS inline (no build step)
├── README.md           # This file
└── templates/          # Reserved for future reference assets
    └── .gitkeep
```

---

## Tech Stack

- **Zero backend** — pure browser, no server, no npm, no build step
- **Gemini 2.0 Flash** for text analysis and prompt generation
- **Gemini Image Generation** for lifestyle shot creation
- **CORS fallback chain** for product page scraping (allorigins → corsproxy.io → codetabs)
- **JSZip** (loaded from CDN on demand) for bulk ZIP download

---

## No Dependencies

Everything loads from CDN at runtime:
- Fonts: Google Fonts (Space Grotesk + Inter)
- ZIP: JSZip (only loaded when downloading all)

No npm, no build tools, no frameworks.
