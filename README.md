# AlphaScreen Pro

AlphaScreen Pro is a single-file institutional-style stock analytics dashboard built in HTML, CSS, and JavaScript. It provides market monitoring, stock analytics, screener workflows, sandbox portfolio tracking, holdings management, and backtesting tools for both Indian and US equity markets.

The app is designed to run directly from `index.html` without a build step.

---

## Features

### 1. Multi-Market Dashboard

- India market support
- USA market support
- Separate IND and USA sub-tabs for:
  - Home
  - Stock Analytics
  - My Holdings
- Independent local storage for IND and USA data

---

### 2. Stock Analytics

Analyze individual tickers with:

- Live or delayed chart/quote data
- Price trend analysis
- RSI, MACD, moving averages, Bollinger Bands
- Fundamental scoring
- Signal analysis
- Chart pattern detection
- Latest news section
- TradingView chart shortcut

#### India ticker handling

Indian tickers are displayed cleanly, for example:

```text
ITC
AHCL
RELIANCE
TCS
```

Internally, the app maps them to Yahoo Finance symbols such as:

```text
ITC.NS
AHCL.NS
RELIANCE.NS
TCS.NS
```

TradingView routes use NSE format:

```text
NSE:ITC
NSE:AHCL
NSE:RELIANCE
```

---

### 3. Reliable News Integration

The app separates news logic for India and USA.

#### India News Sources

For India tickers, the app uses stricter filtering to avoid unrelated global headlines.

Sources include:

- NSE corporate announcements
- Google News RSS India search
- Reliable Indian finance/news domains such as:
  - NSE India
  - BSE India
  - Moneycontrol
  - Economic Times
  - Business Standard
  - Livemint
  - CNBC TV18
  - NDTV Profit
  - Reuters
  - Financial Express
  - The Hindu BusinessLine

If no reliable ticker-specific India news is found, the app avoids showing unrelated generic news.

#### USA News Sources

For US tickers, the app supports:

- Yahoo Finance ticker news
- Google News RSS US search
- Reliable finance/news domains such as:
  - Yahoo Finance
  - Reuters
  - CNBC
  - MarketWatch
  - Barron's
  - WSJ
  - Bloomberg
  - Nasdaq
  - Seeking Alpha

---

### 4. My Holdings

The My Holdings section supports independent India and USA portfolios.

#### India Holdings

- Uses INR currency symbol: `₹`
- Stores data separately from USA holdings
- Supports India tickers like `ITC`, `RELIANCE`, `AHCL`

#### USA Holdings

- Uses USD currency symbol: `$`
- Stores data separately from India holdings
- Supports tickers like `AAPL`, `MSFT`, `NVDA`

---

### 5. Screener

The screener supports India and USA stock scanning with strategies such as:

- Swing Trade
- Momentum Breakout

Screener metrics include:

- Price
- Entry
- Gap %
- Volume surge
- Relative strength
- Trend score
- Signal score
- Stop loss
- Targets
- Confidence
- Strategy tag
- Pattern

---

### 6. Sandbox Portfolio

The sandbox allows trade simulation and portfolio tracking.

Features include:

- Separate India and USA sandbox tabs
- Add trade
- Refresh live prices
- Save snapshot
- Export CSV
- Export JSON
- Import JSON
- INR and USD currency display
- P&L tracking
- Stop loss and target levels

---

### 7. Backtest

The backtest module allows strategy simulation with configurable parameters.

Options include:

- Market selection
  - NSE India
  - US Equities
- Strategy selection
- Period selection
- Capital
- Position size
- Minimum confidence
- Stop loss
- Target

Outputs include:

- KPI summary
- Equity curve
- Monthly returns
- Trade log
- Export option

---

## File Structure

This project is built as a single-page standalone file.

```text
index.html
README.md
```

No build system is required.

---

## How to Run

### Option 1: Open Directly

Download or clone the repository and open:

```text
index.html
```

in a modern browser.

Recommended browsers:

- Google Chrome
- Microsoft Edge
- Brave
- Firefox

---

### Option 2: Run with a Local Server

Some browser features and external data requests may work better through a local server.

Using Python:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/index.html
```

---

## Usage Guide

### Add an India Stock

1. Open `Stock Analytics`
2. Select `IND`
3. Enter ticker:

```text
ITC
```

or

```text
AHCL
```

4. Click `+ Add / Analyze`

The app displays the ticker as `ITC` or `AHCL`, while internally using `ITC.NS` or `AHCL.NS`.

---

### Add a US Stock

1. Open `Stock Analytics`
2. Select `USA`
3. Enter ticker:

```text
AAPL
```

or

```text
MSFT
```

4. Click `+ Add / Analyze`

---

### Save Stock Analytics

Use:

```text
💾 Save Active
```

This saves the currently active market tab independently.

Storage is separated as:

```text
sdp_IND
sdp_US
```

---

### Add India Holdings

1. Open `My Holdings`
2. Select `IND`
3. Enter ticker, average price, quantity, and optional cash balance
4. Click `+ Add Holding`

India holdings use INR formatting.

---

### Add USA Holdings

1. Open `My Holdings`
2. Select `USA`
3. Enter ticker, average price, quantity, and optional cash balance
4. Click `+ Add Holding`

USA holdings use USD formatting.

---

## Local Storage Keys

The app uses browser local storage.

Important keys include:

```text
sdp_IND
sdp_US
myHoldings_IND
myHoldings_US
portfolioCash_IND
portfolioCash_US
asp_theme
```

If stale results appear, use the dashboard's `Reset Cache` button or manually clear browser site data.

---

## Troubleshooting

### Latest News shows unrelated headlines for India stocks

Use the latest version of `index.html` and clear cache.

Recommended steps:

1. Click `Reset Cache`
2. Hard refresh the browser:
   - Windows: `Ctrl + F5`
   - macOS: `Cmd + Shift + R`
3. Re-add the India ticker

If there is no reliable ticker-specific news, the app may show an empty Latest News section instead of unrelated headlines.

---

### India ticker does not fetch data

Confirm the Yahoo Finance NSE symbol exists.

Examples:

```text
ITC -> ITC.NS
AHCL -> AHCL.NS
RELIANCE -> RELIANCE.NS
```

Use the clean ticker in the UI, not the `.NS` suffix.

---

### TradingView chart opens wrong exchange

India tickers are routed as:

```text
NSE:TICKER
```

Example:

```text
NSE:ITC
NSE:AHCL
```

If TradingView still opens incorrectly, clear browser cache and retry.

---

### Data does not refresh

Try:

1. Click `Refresh`
2. Click `Reset Cache`
3. Hard refresh the browser
4. Run through a local server instead of opening the file directly

---

## Browser Permissions

The app fetches public market data and news from external sources. Browser extensions, ad blockers, corporate firewalls, or CORS restrictions may block some requests.

If data does not load properly, try:

- Disabling strict ad blockers for the local file
- Using Chrome or Edge
- Running from a local server
- Checking browser console errors

---

## Technologies Used

- HTML5
- CSS3
- Vanilla JavaScript
- Browser LocalStorage
- Yahoo Finance-compatible data endpoints
- Google News RSS
- NSE corporate announcements
- TradingView external chart links

---

## Disclaimer

This dashboard is for educational, analytical, and personal portfolio tracking purposes only.

It does not provide financial advice, investment recommendations, or guaranteed trading signals. Always verify market data, fundamentals, news, and corporate announcements from official sources before making investment decisions.

Trading and investing involve risk, including possible loss of capital.

---

## Suggested Repository Name

```text
alphascreen-pro
```

---

## Suggested GitHub Description

```text
Single-file India and US stock analytics dashboard with screener, holdings, sandbox portfolio, backtesting, TradingView links, and reliable ticker-specific news.
```

---

## License

You may add a license based on your intended usage.

Common options:

```text
MIT License
```

or

```text
Proprietary / Private Use Only
```

---

## Author

Created and maintained by:

```text
Sethu Lakshminarayanan
```
