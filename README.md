# SmartHeaven Demo Trader (Android, Kotlin + Jetpack Compose)

Groww-style demo / paper trading app. Everything is simulated with **demo money**; nothing touches a real broker.

## Folder layout
All source files sit in ONE folder, numbered in reading order:

`app/src/main/java/com/smartheaven/demotrader/`

| File | What it does |
|---|---|
| F01_Theme | Groww-like dark colours |
| F02_Models | Data classes, instrument list, lot sizes |
| F03_BlackScholes | Option pricing + Delta / Gamma / Theta / Vega / IV |
| F04_MarketEngine | LIVE ticks + REPLAY player, option chain, OI model |
| F05_DhanApi | Optional real data (DhanHQ) with soft fallback |
| F06_TradingEngine | Demo wallet, Market / Limit / SL / SL-M, Target + Stop-loss (OCO), positions, P&L |
| F07_AppViewModel | App state, 1-second market loop |
| F08_Components | Shared UI pieces, candle chart |
| F09_StocksTab | Stocks: Explore / Holdings / Positions / Orders |
| F10_FnoTab | F&O: Explore / Positions / Orders / All watchlists |
| F11_OptionChain | NIFTY + SENSEX chain, OI bars, Greeks, expiry picker, column settings |
| F12_OrderSheet | Buy/Sell sheet with all order types |
| F13_PositionsOrders | Positions (exit, add target/SL), order book (modify/cancel) |
| F14_WalletAndMarket | Demo money (add / withdraw / set any amount), LIVE-REPLAY bar, Dhan keys |
| F15_DetailAndWatchlist | Instrument page, search, watchlist |
| F16_MfAndLoans | Static demo screens |
| F17_MainActivity | Entry point |

## Build the APK (no Android Studio needed)
1. Push this folder to a GitHub repo (branch `main`).
2. Open **Actions → Build SmartHeaven APK → Run workflow** (it also runs on every push).
3. Download the `SmartHeaven-debug-apk` artifact.

Or locally: open in Android Studio and press Run.

## Using it
- **Demo money**: avatar/wallet icon (top right) → Add money / Withdraw / **Set balance to any amount**.
- **LIVE / REPLAY**: chips under the title. Replay has date, play/pause, 1x-60x speed and a seek slider.
- **Orders**: tap a CE/PE cell in the option chain, or Buy/Sell on any stock/commodity. Choose Market, Limit, SL or SL-M, and optionally set Target and Stop-loss. You can also add Target/SL later from Positions.
- **Option chain**: gear icon picks columns (LTP, OI, OI Chg, Vol, IV, Gamma, Vega, Theta, Delta); bar icon shows the candle chart.

## Data notes
- Without keys, prices, OI and replay days are simulated (option prices/Greeks come from Black-Scholes, OI is a synthetic curve).
- With DhanHQ keys: LIVE uses real NIFTY/SENSEX LTP and the real option chain (OI, IV, Greeks); REPLAY tries real 1-minute candles. Any failure falls back to the simulator.
- Lot sizes: edit `Universe` in F02_Models (NIFTY 75, SENSEX 20 by default; confirm current exchange lot sizes).
