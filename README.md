# ₿ BTC Decision Dashboard

A single-file, dark-themed dashboard that helps you decide **when to buy more Bitcoin**.
Pure HTML/CSS/JS — no backend, no build step, no dependencies. Open the file in any
browser and it works.

👉 **[`btc-decision-helper.html`](./btc-decision-helper.html)**

## Features

- **Live BTC price (EUR)** with a 30-day sparkline, the 30-day high, and the current
  **% drop from that high** shown prominently.
- **Fear & Greed Index** (0–100) on a colour-coded gauge:
  dark-green = Extreme Fear, green = Fear, orange = Neutral, red = Greed, deep-red = Extreme Greed.
- **Buy signal** that combines both metrics:
  | Signal | Condition |
  | --- | --- |
  | 🟢 **STRONG BUY** | Fear & Greed `< 25` **and** price `> 10%` below the 30-day high |
  | 🟡 **CONSIDER BUYING** | either one of those is true |
  | ⬜ **HOLD** | neither is true |
- **Moving averages & dip zones** — 30 / 50 / 200-day moving averages with a plain-English
  "buy the dip" (BTFD) read-out (deep-value / buy-the-dip / minor-dip / extended) and
  golden-cross vs death-cross trend.
- **Telegram alerts** — one button sends the current signal + stats to your phone.
- **Resilient** — automatic fallback across data providers, request timeouts with retry,
  and a local cache so the last known values still show if every API is down.
- **Auto-refresh** every 5 minutes (plus a manual refresh and a refresh-on-focus).
- **Mobile-friendly** responsive layout, accessible labels, reduced-motion support.

## Data sources (all free, all client-side)

| Data | Primary | Fallbacks |
| --- | --- | --- |
| Price | CoinGecko | Binance → Coinbase |
| 30-day high & sparkline | CoinGecko OHLC | Binance klines |
| Fear & Greed | Alternative.me | (cached) |

If a provider rate-limits or fails, the dashboard transparently tries the next one and
shows which source served the price.

## Telegram setup

1. In Telegram, message **@BotFather** → `/newbot` → copy the **Bot Token**.
2. Message **@userinfobot** → copy your numeric **Chat ID**.
3. Open the dashboard → **Configure Telegram Settings** → paste both → **Send Alert to Telegram**.

Your token and chat ID are stored only in your browser's `localStorage` and are sent
directly to Telegram's API — they never touch any server of mine.

## Running / hosting

- **Locally:** just double-click `btc-decision-helper.html`.
- **GitHub Pages:** push this repo, enable Pages (Settings → Pages → deploy from `main`),
  then visit `https://<user>.github.io/btc-dashboard/btc-decision-helper.html`.

## Privacy & disclaimer

No analytics, no cookies, no backend. All API calls go straight from your browser to the
public providers above.

This tool is for **informational purposes only** and is **not financial advice**.
Cryptocurrency is volatile; do your own research.
