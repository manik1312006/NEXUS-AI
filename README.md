# NEXUS AI — Multi-Agent Intelligence Hub

A web-based chat platform that lets you talk to multiple AI models from a single interface, with a built-in Prompt Enhancer that rewrites your queries before sending them for better results.

---

## Features

- **9 AI Agents** — GPT-OSS 120B (NVIDIA NIM), LLaMA 3.3 70B (NVIDIA NIM), Kimi K2.6 (NVIDIA NIM), Gemma 4 31B IT (NVIDIA NIM), Gemini Flash, Mistral Large, Codestral, LLaMA 3.3 (via Groq), and Cohere Command R+
- **Concise Structured Responses** — all AI agents are instructed to answer briefly by default with focused bullets or compact paragraphs, while still expanding when the task requires depth
- **Prompt Enhancer** — automatically rewrites your prompt using LLaMA (free) before sending it to the chosen agent
- **Smart Web Grounding** — comprehensive regular-expression-based checker matching temporal indicators, comparisons, explicit search commands, and factual question formats to automatically fetch live context
- **Organic DDG Scraper** — a custom backend organic HTML DuckDuckGo scraper that retrieves true URLs and rich snippets without API keys or rate limits
- **Deep Research Engine** — multi-branch exploration with step-by-step reasoning, tree visualization, automatic branch-level web searches, synthesis grounding, and exportable structured Markdown reports
- **Gapless Voice Narration (TTS)** — sequential 10-word chunking with an asynchronous in-memory pre-buffering queue (preloading 2 chunks ahead as local Blob URLs) for continuous zero-lag speech playback
- **🌗 Dark / Light Mode** — one-click theme toggle (🌙/☀️) in the top-right corner of every page; preference is saved to `localStorage` and persists across sessions and page navigations
- **Voice Input** — speak your message with real-time waveform visualization, confidence scoring, and transcript editing before sending
- **AI Memory** — automatically extracts and stores key facts from conversations, injected as context in future sessions (Google accounts only)
- **Secure backend** — all API keys live on the server (Node/Express on Render), never exposed to the browser
- **Authentication** — Google Sign-In or instant Anonymous (Guest) login via Firebase Auth
- **Chat history** — sessions saved per user in Firebase Realtime Database, last 20 chats accessible from the sidebar
- **Fully responsive** — works on desktop, tablet, and mobile with a slide-in sidebar and iOS safe-area support
- **Syntax highlighting** — code blocks rendered with highlight.js and markdown parsed with marked.js

---

## Dark / Light Mode

| Control | Location |
|---|---|
| Landing page toggle | Top-right of the navbar (next to BETA badge) |
| Chat page toggle | Top-right of the main header (next to status badges) |

- **Dark mode** (default) — deep navy/black background with neon purple, cyan, and pink accents
- **Light mode** — soft lavender/white background with adjusted accent colors for readability
- The selected theme is saved to `localStorage` under the key `nexus-theme` and automatically applied on every page load — no flash of unstyled content (FOUC)

---

## Project Structure

```
nexus-ai/
├── server.js          # Express backend — all API keys live here
├── package.json       # Node dependencies (express, cors, dotenv)
├── .env               # API keys — never commit this
├── .gitignore
├── index.html         # Landing page + authentication (Google / Guest)
└── pages/
    └── chat.html      # Main chat interface (agents, memory, voice, research)
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML/CSS/JS |
| Backend | Node.js + Express, hosted on Render |
| Auth | Firebase Authentication (Google + Anonymous) |
| Database | Firebase Realtime Database (chat history + memories) |
| AI APIs | NVIDIA NIM (OpenAI-compat), Google Gemini, Mistral, Codestral, Groq, Cohere |
| Markdown | marked.js + highlight.js |
| Theme | CSS custom properties + `localStorage` persistence |

---

## Setup

### 1. Clone the repo

```bash
git clone https://github.com/manik1312006/NEXUS-AI.git
npm install
```

### 2. Create your `.env` file

```env
NVIDIA_KEY_GPTOSS=...
NVIDIA_KEY_LLAMA=...
NVIDIA_KEY_DEEPSEEK=...
GEMINI_API_KEY=AIza...
MISTRAL_API_KEY=...
CODESTRAL_API_KEY=...
GROQ_API_KEY=gsk_...
COHERE_API_KEY=...
PORT=4000
```

You don't need all keys — the server returns a clear error for any agent whose key is missing. Groq is free and powers the Prompt Enhancer, so that one is recommended.

### 3. Run locally

```bash
npm run dev       # uses node --watch for auto-reload
# or
npm start
```

Backend runs at `http://localhost:4000`. Open `index.html` directly in a browser or use VS Code Live Server (`http://127.0.0.1:5500`).

### 4. Firebase setup

1. Create a project at [firebase.google.com](https://firebase.google.com)
2. Enable **Authentication → Sign-in methods → Google** and **Anonymous**
3. Enable **Realtime Database** and set rules to allow authenticated reads/writes
4. Copy your Firebase config into both `index.html` and `pages/chat.html`

### 5. Deploy the backend (Render)

1. Push your code to GitHub (`.env` is gitignored — add keys via Render's Environment tab)
2. Create a new **Web Service** on [render.com](https://render.com), connect your repo
3. Set build command: `npm install` and start command: `npm start`
4. Add all your API keys as environment variables in Render's dashboard
5. Update the `BACKEND` constant in `pages/chat.html` to your Render URL

### 6. Deploy the frontend (Netlify)

Drop the `index.html` and `pages/` folder into [netlify.com](https://netlify.com) via drag-and-drop, or connect your GitHub repo. Update the CORS `origin` list in `server.js` to include your Netlify URL.

---

## API Routes

| Method | Route | Agent / Feature | Notes |
|---|---|---|---|
| POST | `/api/openai` | GPT-OSS 120B (NVIDIA NIM) | Requires `{ messages }` |
| POST | `/api/nvidia-llama` | LLaMA 3.3 70B (NVIDIA NIM) | Requires `{ messages }` |
| POST | `/api/deepseek` | Kimi K2.6 (NVIDIA NIM) | Requires `{ messages }` |
| POST | `/api/gemma4` | Gemma 4 31B IT (NVIDIA NIM) | Requires `{ messages }` |
| POST | `/api/gemini` | Gemini Flash | Requires `{ prompt }` |
| POST | `/api/mistral` | Mistral Large | Requires `{ messages }` |
| POST | `/api/codestral` | Codestral | Requires `{ messages }` |
| POST | `/api/groq` | LLaMA 3.3 (Groq) | Requires `{ messages }` |
| POST | `/api/cohere` | Command R+ | Requires `{ prompt }` |
| POST | `/api/enhance` | LLaMA 3.3 (Groq) | Prompt enhancer, falls back to OpenAI |
| POST | `/api/deep-research` | Multi-agent | Deep Research Engine (SSE stream) |
| POST | `/api/search` | Smart Web Search | Auto-selects Tavily ➔ SerpAPI ➔ DuckDuckGo |
| POST | `/api/search/duckduckgo` | DuckDuckGo Search | Custom Organic HTML DDG Scraper (Free) |
| POST | `/api/tts-script` | TTS Speech Rewriter | Adapts raw responses into vocal scripts |
| POST | `/api/tts` | Murf AI Speech Proxy | Proxies MP3 voice generation securely |
| GET | `/` | — | Health check |

---

## AI Agent Status

| Agent | Free Tier | Notes |
|---|---|---|
| LLaMA 3.3 (Groq) | ✅ Yes | Generous free tier, also powers the Prompt Enhancer |
| NVIDIA NIM (LLaMA 3.3 70B) | ✅ Trial credits | Free credits on sign-up |
| NVIDIA NIM (GPT-OSS 120B) | ✅ Trial credits | OpenAI-compatible endpoint |
| NVIDIA NIM (Kimi K2.6) | ✅ Trial credits | Requires `NVIDIA_KEY_KIMI` on the backend |
| NVIDIA NIM (Gemma 4 31B IT) | ✅ Trial credits | Requires `NVIDIA_KEY_GEMMA4` on the backend |
| Mistral Large | ✅ Trial credits | Free trial on sign-up |
| Codestral | ✅ Separate key | Uses `CODESTRAL_API_KEY` and `https://codestral.mistral.ai/v1/chat/completions` |
| Cohere Command R+ | ✅ Trial credits | v2/chat API |
| Gemini Flash | ⚠️ Daily quota | Free via AI Studio key; quota resets daily |

---

## Environment Variables

| Variable | Where to get it |
|---|---|
| `NVIDIA_KEY_GPTOSS` | [build.nvidia.com](https://build.nvidia.com) |
| `NVIDIA_KEY_LLAMA` | [build.nvidia.com](https://build.nvidia.com) |
| `NVIDIA_KEY_DEEPSEEK` | [build.nvidia.com](https://build.nvidia.com) |
| `NVIDIA_KEY_GEMMA4` | [build.nvidia.com](https://build.nvidia.com) |
| `GEMINI_API_KEY` | [aistudio.google.com](https://aistudio.google.com) |
| `MISTRAL_API_KEY` | [console.mistral.ai](https://console.mistral.ai) |
| `CODESTRAL_API_KEY` | [console.mistral.ai](https://console.mistral.ai) / Codestral API key |
| `GROQ_API_KEY` | [console.groq.com](https://console.groq.com) |
| `COHERE_API_KEY` | [dashboard.cohere.com](https://dashboard.cohere.com) |

---

## Known Limitations

- Anonymous (Guest) sessions are tied to the browser — clearing site data loses the session
- AI Memory is only available for Google-authenticated users (not guests)
- Chat history is stored unencrypted in Firebase Realtime Database
- The Prompt Enhancer adds ~1–2 seconds of latency per message when enabled
- The Deep Research Engine makes multiple sequential API calls — response time varies with topic complexity

---

## Author

**Manik Mehta**
- Student
- 20 years old
- 📍 Fatehabad, Haryana, India
- 📧 manikmehtaji@gmail.com
- ⌥ [GitHub](https://github.com/manik1312006)

---
