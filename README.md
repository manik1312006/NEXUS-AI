# NEXUS AI — Multi-Agent Intelligence Hub

A web-based chat platform that lets you talk to six different AI models from a single interface, with a built-in Prompt Enhancer that rewrites your queries before sending them for better results.

---

## Features

- **6 AI Agents** — GPT-4o, Claude 3.5, Gemini 2.0 Flash, Mistral Large, LLaMA 3.3 (via Groq), and Cohere Command R+
- **Prompt Enhancer** — automatically rewrites your prompt using LLaMA (free) before sending it to the chosen agent
- **Secure backend** — all API keys live on the server (Node/Express on Render), never exposed to the browser
- **Authentication** — Google Sign-In or instant Anonymous (Guest) login via Firebase Auth
- **Chat history** — sessions saved per user in Firebase Realtime Database, last 20 chats accessible from the sidebar
- **Fully responsive** — works on desktop, tablet, and mobile with a slide-in sidebar and iOS safe-area support
- **Syntax highlighting** — code blocks rendered with highlight.js and markdown parsed with marked.js

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
    └── chat.html      # Main chat interface
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML/CSS/JS |
| Backend | Node.js + Express, hosted on Render |
| Auth | Firebase Authentication (Google + Anonymous) |
| Database | Firebase Realtime Database (chat history) |
| AI APIs | OpenAI, Anthropic, Google Gemini, Mistral, Groq, Cohere |
| Markdown | marked.js + highlight.js |

---

## Setup

### 1. Clone the repo

```bash
git clone https://github.com/your-username/nexus-ai.git
cd nexus-ai
npm install
```

### 2. Create your `.env` file

```env
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
GEMINI_API_KEY=AIza...
MISTRAL_API_KEY=...
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

| Method | Route | Agent | Notes |
|---|---|---|---|
| POST | `/api/openai` | GPT-4o | Requires `{ messages }` |
| POST | `/api/claude` | Claude 3.5 Sonnet | Requires `{ messages }` |
| POST | `/api/gemini` | Gemini 2.0 Flash | Requires `{ prompt }` |
| POST | `/api/mistral` | Mistral Large | Requires `{ messages }` |
| POST | `/api/groq` | LLaMA 3.3 70B | Requires `{ messages }` |
| POST | `/api/cohere` | Command R+ | Requires `{ prompt }` |
| POST | `/api/enhance` | LLaMA 3.3 (Groq) | Prompt enhancer, falls back to OpenAI |
| GET | `/` | — | Health check |

---

## AI Agent Status

| Agent | Free Tier | Notes |
|---|---|---|
| LLaMA 3.3 via Groq | ✅ Yes | Generous free tier, also powers the Prompt Enhancer |
| Mistral Large | ✅ Trial credits | Free trial on sign-up |
| Cohere Command R+ | ✅ Trial credits | Migrated to v2/chat API (Sept 2025) |
| Gemini 2.0 Flash | ⚠️ Daily quota | Free via AI Studio key; quota resets daily |
| GPT-4o | ❌ Paid | Requires OpenAI billing ($5 minimum top-up) |
| Claude 3.5 Sonnet | ❌ Paid | Requires Anthropic credits |

---

## Environment Variables

| Variable | Where to get it |
|---|---|
| `OPENAI_API_KEY` | [platform.openai.com/api-keys](https://platform.openai.com/api-keys) |
| `ANTHROPIC_API_KEY` | [console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys) |
| `GEMINI_API_KEY` | [aistudio.google.com](https://aistudio.google.com) |
| `MISTRAL_API_KEY` | [console.mistral.ai](https://console.mistral.ai) |
| `GROQ_API_KEY` | [console.groq.com](https://console.groq.com) |
| `COHERE_API_KEY` | [dashboard.cohere.com](https://dashboard.cohere.com) |

---

## Known Limitations

- Anonymous (Guest) sessions are tied to the browser — clearing site data loses the session
- Chat history is stored unencrypted in Firebase Realtime Database
- The Prompt Enhancer adds ~1–2 seconds of latency per message when enabled

---

## Author

**Manik Mehta**
- Student
- 20 years old
- 📍 Fatehabad, Haryana, India
- 📧 manikmehtaji@gmail.com
  
---
