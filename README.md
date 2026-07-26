<div align="center">

# 🛰️ NexusBot

**A premium Discord bot platform with a real-time management dashboard.**

Built as a full-stack showcase — a discord.js v14 bot and a polished React control center,
wired together with OAuth2, WebSockets and a clean, layered architecture.

`TypeScript` · `discord.js v14` · `Express` · `MongoDB` · `Socket.IO` · `React` · `Vite` · `TailwindCSS`

</div>

---

## ✨ Highlights

|  | Feature |
|--|---------|
| 🔐 | **Discord OAuth2** login → pick a server you manage → open its dashboard |
| 📊 | **Live dashboard** — member counts, bot ping, uptime, CPU/RAM & DB status streamed over WebSockets |
| 🛡️ | **Moderation** — ban, kick, timeout, warn, unban, purge, slowmode, lock/unlock — every action stored as a numbered case |
| 👋 | **Welcome system** — channel picker, embed builder, variable support and a pixel-accurate live preview |
| 📈 | **Analytics** — command usage and moderation trends in interactive charts |
| ⚙️ | **Settings** — prefix, language and embed colour, persisted per guild |
| 🤖 | **14 slash commands** — moderation + utility (`serverinfo`, `userinfo`, `avatar`, `ping`, `help`) |
| 📚 | **Auto-generated API docs** (OpenAPI / Swagger UI) |
| 🐳 | **Docker-first** — `docker compose up` brings up Mongo + API + dashboard |

## 🧱 Tech stack

**Backend** — Node.js 22, TypeScript, discord.js v14, Express, MongoDB + Mongoose, Passport
(Discord OAuth2), JWT (httpOnly cookies), Socket.IO, Zod, Helmet, Winston, Swagger.

**Frontend** — React 18, Vite, TypeScript, TailwindCSS, Framer Motion, Recharts, React Router,
TanStack Query, Lucide icons.

**Tooling** — npm workspaces, ESLint, Prettier, Husky + lint-staged, GitHub Actions CI, Docker.

## 📂 Project structure

```
nexusbot/
├── apps/
│   ├── server/            # API + realtime gateway + Discord bot (TypeScript)
│   │   └── src/
│   │       ├── bot/        # client, command & event loaders, commands, events
│   │       ├── config/     # env validation (zod) + constants
│   │       ├── db/         # Mongoose connection + models
│   │       ├── repositories/  # data-access layer
│   │       ├── services/   # business logic (auth, guild, moderation, welcome, stats)
│   │       └── http/       # express app, middleware, controllers, routes, socket, swagger
│   └── web/               # React dashboard (Vite)
│       └── src/
│           ├── components/ # ui/ layout/ charts/ common/
│           ├── context/    # auth provider
│           ├── hooks/      # data hooks (TanStack Query + realtime)
│           ├── pages/      # landing, login, server picker, dashboard/*
│           └── lib/        # api client, socket, utils
├── docs/                  # SETUP · ARCHITECTURE · DEPLOYMENT
├── docker-compose.yml
└── package.json           # npm workspaces root
```

## 🚀 Quick start

> **Prerequisites:** Node.js ≥ 20, a MongoDB instance (local or Atlas), and a Discord application.
> The full walkthrough — including the Discord Developer Portal — is in **[`docs/SETUP.md`](docs/SETUP.md)**.

```bash
# 1. Install dependencies (npm workspaces)
npm install

# 2. Configure environment
cp apps/server/.env.example apps/server/.env   # fill in Discord + Mongo details
cp apps/web/.env.example    apps/web/.env

# 3. Register the bot's slash commands
npm run deploy:commands

# 4. Run the API + bot and the dashboard together
npm run dev
```

- Dashboard → <http://localhost:5173>
- API → <http://localhost:8080>
- API docs → <http://localhost:8080/api/docs>

### 🐳 …or with Docker

```bash
cp .env.example .env        # fill in Discord credentials
docker compose up --build
```

Brings up MongoDB, the API/bot and the dashboard (served by nginx). See
**[`docs/DEPLOYMENT.md`](docs/DEPLOYMENT.md)**.

## 📜 Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Run API/bot and dashboard concurrently |
| `npm run build` | Type-check and build both apps |
| `npm run deploy:commands` | Register slash commands with Discord |
| `npm run lint` / `npm run format` | Lint / format the whole monorepo |
| `npm run typecheck` | Type-check both apps |

## 🗺️ Roadmap

The codebase is structured so each feature is a vertical slice
(model → repository → service → controller → route, plus a page and a bot command/event).
Planned modules that follow the same pattern:

- 🎫 Ticket system (panels, buttons/dropdowns, transcripts, claim/close/reopen)
- 📝 Logging (message edits/deletes, joins/leaves, voice, roles)
- 🎭 Reaction roles (buttons + select menus)
- 💡 Suggestions (upvote/downvote, status changes, staff responses)
- 👑 Owner admin panel (global stats, guild list, broadcast, maintenance mode)

## 📄 License

MIT © 2026 Veer — see [`LICENSE`](LICENSE).
