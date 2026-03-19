# Odosa's Machine

A live Bitcoin candle analysis tool that connects directly to Binance to scan and rank every 15-minute candle window by consistency score — finding the most predictable directional bias and mirror pair correlations across the trading day.

---

## Live site

**Main tool:** https://oxdonyosa.github.io/odosas-machine

**Backtest data export:** https://oxdonyosa.github.io/odosas-machine/backtest.html

---

## Features

- **Consistency scanner** — Scans all 96 daily 15-min windows and ranks them by directional bias (bullish or bearish), not just green close rate
- **Mirror pair engine** — Identifies windows that close in the same direction consistently on the same day (e.g. if 09:00 ET closes red, does 14:00 ET close red too?)
- **Your target window** — Compare your chosen candle against every other window in the day
- **Mon–Fri or All 7 days** — Toggle weekend candles in or out with one click
- **Local time equivalent** — Every ET time is converted to your timezone (WAT or any offset) automatically, DST-aware
- **Backtest export** — Export full candle history to CSV or JSON for deeper analysis
- **No backend, no login** — Runs entirely in the browser using Binance's public API
- **Live data** — Pulls fresh candle data every time you run it

---

## How to use

1. Visit https://oxdonyosa.github.io/odosas-machine
2. Expand **Parameters** and set your symbol, interval, target time, lookback period and timezone
3. Choose **MON–FRI** or **ALL 7 DAYS** mode
4. Hit **RUN**
5. Read the results across three tabs:
   - **Target Candles** — your specific window's history and off-bias days
   - **Mirror Pairs** — windows that mirror your target's direction
   - **All Windows** — every window ranked by consistency score

For backtest data, visit https://oxdonyosa.github.io/odosas-machine/backtest.html and export your results as CSV or JSON.

---

## Parameters

| Parameter | Description |
|---|---|
| Symbol | Trading pair (BTCUSDT, ETHUSDT, SOLUSDT, BNBUSDT, XRPUSDT) |
| Interval | Candle size — 5m, 15m, 30m, 1h |
| Target time (ET) | The specific window you want to analyse e.g. `09:00` |
| Lookback period | How far back to scan — 1, 2, 3, 6, or 12 months |
| Timezone offset | Your UTC offset e.g. `+1` for WAT (Abuja) |
| Timezone label | Display label e.g. `WAT` |
| Min days | Minimum days a window needs before it qualifies in the ranking |

---

## Consistency score explained

The consistency score is the percentage of days a window closes in its dominant direction — whether that's green or red. A window that closes red 85% of the time scores 85%, just as valuable as one that closes green 85%. This makes the ranking direction-agnostic and purely about predictability.

---

## Mirror score explained

For any two windows A and B, the mirror score is the percentage of days both candles closed in the same direction (both green or both red) on the same calendar day. A score of 80%+ means if you know what A does, you have an 80% probability of predicting B.

---

## Tech stack

- Vanilla HTML, CSS, JavaScript — zero dependencies
- Binance public REST API (`/api/v3/klines`) — no API key required
- Google Fonts (Space Mono + Syne)

---

## License

MIT License — see `LICENSE` for details.

---

Built by [@donyosa](https://twitter.com/donyosa)
