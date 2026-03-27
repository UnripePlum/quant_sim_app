<div align="center">

<h1><b>Quant Sim</b></h1>
<p><b>A risk-free stock trading simulator with real-time charts and Google OAuth.</b></p>

<p>
  <a href="#features"><strong>Features</strong></a> ·
  <a href="#tech-stack"><strong>Tech Stack</strong></a> ·
  <a href="#getting-started"><strong>Getting Started</strong></a> ·
  <a href="#related"><strong>Related</strong></a>
</p>

<p>

[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js&logoColor=white)](https://nextjs.org)
[![License](https://img.shields.io/badge/license-MIT-blue)](./LICENSE)

</p>

</div>

---

## Overview

Quant Sim is a browser-based trading simulator that lets users practise buying and selling assets without real financial risk. After signing in with Google, users get a virtual cash balance, place limit and market orders, and watch their portfolio performance update in real time via WebSocket price feeds.

> [!NOTE]
> This is the frontend application. It requires the [quant_sim_backend](https://github.com/UnripePlum/quant_sim_backend) to be running for order execution and user data.

## Features

<details>
<summary><b>Authentication</b></summary>

- Google OAuth sign-in via NextAuth.js — no password required
- Protected routes automatically redirect unauthenticated users to `/login`
- Session-aware user context persisted across page navigations

</details>

<details>
<summary><b>Trading</b></summary>

- Place **limit** and **market** orders (buy and sell)
- Quick-order buttons at 10 %, 25 %, 50 %, and 100 % of available balance
- Real-time order book and recent trade history per symbol
- Balance validation before order submission with inline error feedback

</details>

<details>
<summary><b>Charts & Market Data</b></summary>

- Live candlestick chart powered by [Lightweight Charts](https://tradingview.github.io/lightweight-charts/) with throttled WebSocket updates
- Volume bars rendered alongside price candles
- Portfolio value line chart with 1D / 5D / 1M / 6M / 1Y / Max time ranges
- Mini chart and market depth views in the quick-order panel

</details>

<details>
<summary><b>Dashboard</b></summary>

- Current cash balance and total invested amount cards
- Holdings list with per-asset quantity and current value
- Responsive grid layout — single column on mobile, three columns on desktop

</details>

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | [Next.js 14](https://nextjs.org) (App Router) |
| Language | [TypeScript 5](https://www.typescriptlang.org) |
| Styling | [Tailwind CSS 3](https://tailwindcss.com) |
| Auth | [NextAuth.js 4](https://next-auth.js.org) — Google provider |
| Charts | [Lightweight Charts 5](https://tradingview.github.io/lightweight-charts/), [Recharts 3](https://recharts.org) |
| Data | WebSocket (real-time prices via backend) |
| Utilities | [Lodash](https://lodash.com) (throttle) |

## Getting Started

### Prerequisites

- Node.js 18 or later
- A running instance of [quant_sim_backend](https://github.com/UnripePlum/quant_sim_backend)
- A Google OAuth application (Client ID + Secret)

### Installation

```bash
git clone https://github.com/UnripePlum/quant_sim_app.git
cd quant_sim_app
npm install
```

### Environment Variables

Create a `.env.local` file in the project root:

```env
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your_secret_here

GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

NEXT_PUBLIC_API_BASE_URL=http://localhost:8000
```

> [!TIP]
> Generate `NEXTAUTH_SECRET` with `openssl rand -base64 32`.

### Run

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

```bash
npm run build   # production build
npm start       # serve production build
```

## Related

- [quant_sim_backend](https://github.com/UnripePlum/quant_sim_backend) — REST + WebSocket API that powers order matching, user accounts, and real-time price feeds

## License

MIT
