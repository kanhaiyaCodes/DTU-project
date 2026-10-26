# Message Saathi AI

**Understand every message. In your language.**

Message Saathi is a mobile-friendly, open-source web prototype that helps people understand confusing SMS and other text messages. It provides a plain-language explanation, Hindi/Hinglish output, practical next steps, and potential scam-warning signals.

## Features

- Responsive HTML/CSS/JavaScript interface
- Paste a message or try sample electricity, bank, and suspicious-message examples
- Simple explanation, translation, suggested actions, and safety signals
- Browser text-to-speech for the explanation
- Copyable summary
- Optional Google Generative Language API connection for Gemma-family models
- Local demo mode works without an API key
- No database and no message history storage

## Run locally

No build step is required.

1. Download or clone this repository.
2. Open `index.html` in a modern browser.
3. Click a sample message and press **Understand message**.

For more reliable browser behavior, serve the folder using VS Code Live Server or run `python -m http.server 8000` from this folder, then open `http://localhost:8000`.

## Enable live AI

1. Create an API key through Google AI Studio, if API access is available for your account.
2. Open the website and choose the gear icon.
3. Paste the key for this browser tab.
4. Enter the exact model identifier supported by your API key and account, then save.
5. Try a message. If the model/API call fails, the website falls back to the local demo analysis and displays an error.

**Model availability note:** The default field uses `gemma-3-27b-it` as a compatibility example. It does not claim that this model is Gemma 4. Before submission, check the official model list and use the exact Gemma 4 model ID if it is actually available to your account and supports the Generative Language API. Do not claim a live Gemma 4 integration unless you test it successfully.

## Security and privacy notes

- The demo does not store messages in a database or local storage.
- When a user supplies an API key, it remains in JavaScript memory for the current page session. API requests send the message and key to Google's API.
- This client-side API-key flow is for a quick local/hackathon demo only. It is **not suitable for a public production deployment**, because browser users can inspect client-side requests and keys.
- For public live-AI hosting, add a backend proxy (for example, a small serverless function) and store the key as a server-side environment variable. Add rate limits and abuse protection.
- Never paste real OTPs, passwords, PINs, full account numbers, or sensitive personal information.
- The safety checker is not a security scanner and cannot determine with certainty whether a message is genuine. Verify through official channels.

## Deploy free

### GitHub Pages (static demo)
1. Create a public GitHub repository and upload `index.html`, `styles.css`, `app.js`, and `README.md`.
2. Open **Settings → Pages**.
3. Select **Deploy from a branch**, choose `main` and `/ (root)`, then save.
4. Wait for the published URL and test it on mobile.

GitHub Pages serves the static demo. Live API requests may be limited by model/API availability and should not use a private production key in public client-side code.

Alternative static hosting: Netlify Drop or Cloudflare Pages.

## Suggested hackathon pitch

> Message Saathi is an AI-powered digital-literacy assistant for people who struggle to understand messages in English. It explains a message in simple language, translates it, reads it aloud, and highlights warning signs so users can make more informed decisions. The prototype is designed around accessibility, privacy, and practical next steps.

## Open-source license

This project is intended to be released under the MIT License. Add a `LICENSE` file with the standard MIT text and your chosen copyright holder/year before submitting.

## Current limitations

- SMS and WhatsApp are not automatically read. The user must paste a message.
- No account system, cloud storage, or message synchronization.
- Demo mode uses lightweight rules and example templates, not a trained AI model.
- The app does not verify senders, URLs, bills, transactions, or real-world facts.
- Live model support depends on the exact API/model access available to the developer.
