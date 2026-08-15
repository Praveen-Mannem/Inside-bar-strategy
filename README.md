# Inside Bar Strategy & Stock Screener for TradingView (NSE - Daily & Weekly)

This repository contains **Pine Script v5** scripts implementing the exact **Inside Bar Price Action Trading Strategy** described on [PriceAction.com](https://priceaction.com/price-action-university/strategies/inside-bar/).

It is specially optimized for **NSE (National Stock Exchange of India)** stocks on **Daily (D)** and **Weekly (W)** timeframes and designed to work seamlessly within **TradingView's Free Plan**.

---

## Included Pine Script Files

| File Name | Script Type | Description |
|---|---|---|
| [`Inside_Bar_Strategy.pine`](file:///Users/praveen/Documents/Inside%20bar%20Strategy/Inside_Bar_Strategy.pine) | **Strategy** | Full backtester script with historical win-rate, net profit, drawdown, R:R targets, and order execution. |
| [`Inside_Bar_Screener_Indicator.pine`](file:///Users/praveen/Documents/Inside%20bar%20Strategy/Inside_Bar_Screener_Indicator.pine) | **Indicator + Screener** | Visual pattern overlay + **On-Chart Screener Dashboard** scanning Top 20 NSE stocks on Daily & Weekly + TV Free Plan Alerts. |

---

## Strategy Rules & Mechanics

### 1. What is an Inside Bar Pattern?
- **Mother Bar (MB)**: The prior candlestick (`t-1`).
- **Inside Bar (IB)**: Current bar (`t`) whose range is completely contained within the Mother Bar's range (`High[t] < High[t-1]` and `Low[t] > Low[t-1]`).
- **Coiling / Double Inside Bar**: A second inside bar contained inside the previous inside bar. Shows maximum market consolidation before an explosive breakout.

### 2. Trend Continuation Filter (50 EMA)
- **Bullish Inside Bar Setup**: Price is above the 50 EMA (or EMA slope is positive). Buy Stop entry placed at **Mother Bar High**.
- **Bearish Inside Bar Setup**: Price is below the 50 EMA. Sell Stop entry placed at **Mother Bar Low**.

### 3. Entry, Stop Loss (SL), and Take Profit (TP)
- **Long Entry**: Stop order at `Mother Bar High`.
- **Short Entry**: Stop order at `Mother Bar Low`.
- **Stop Loss Placement**: 
  - Option A: **Classic Extreme** — Below Mother Bar Low (for Longs) or above Mother Bar High (for Shorts).
  - Option B: **50% Midpoint** — Halfway point of the Mother Bar `(MB High + MB Low) / 2` for tighter risk management when Mother Bar is large.
- **Take Profit Target**: Calculated dynamically based on user-defined Risk:Reward Ratio (default `1 : 2.0`).

---

## How to Install in TradingView (Free Plan)

### Step 1: Open TradingView
1. Go to [TradingView.com](https://www.tradingview.com/) and open any NSE chart (e.g., `NSE:RELIANCE` or `NSE:NIFTY`).
2. Set the chart timeframe to **Daily (`1D`)** or **Weekly (`1W`)**.

### Step 2: Open Pine Editor
1. Click on the **Pine Editor** tab at the bottom panel of TradingView.
2. Clear any existing code in the editor.

### Step 3: Copy & Paste Code
- For Backtesting: Copy the entire contents of [`Inside_Bar_Strategy.pine`](file:///Users/praveen/Documents/Inside%20bar%20Strategy/Inside_Bar_Strategy.pine).
- For Live Scanning & Chart Highlights: Copy the entire contents of [`Inside_Bar_Screener_Indicator.pine`](file:///Users/praveen/Documents/Inside%20bar%20Strategy/Inside_Bar_Screener_Indicator.pine).

### Step 4: Save & Add to Chart
1. Click **Save** in top right of Pine Editor.
2. Click **Add to Chart**.

---

## How to Use the On-Chart NSE Screener Table

The indicator script includes a built-in **On-Chart Screener Dashboard** that scans **Top 20 Liquid NSE Stocks** simultaneously:

1. Look at the **Top Right** corner of your chart.
2. The table displays:
   - **Symbol**: `RELIANCE`, `TCS`, `INFY`, `HDFCBANK`, `SBIN`, `NIFTY`, etc.
   - **Timeframe**: `D` (Daily) or `W` (Weekly).
   - **Status**:
     - `★ BULLISH IB` (Green): Inside Bar formed in an uptrend. High-probability Buy setup!
     - `★ BEARISH IB` (Red): Inside Bar formed in a downtrend. High-probability Sell setup!
     - `▲ BULL BREAKOUT` (Teal): Price just broke out above Mother Bar High.
     - `▼ BEAR BREAKDOWN` (Maroon): Price just broke down below Mother Bar Low.
3. **Customization**: Open script settings -> **NSE Screener Dashboard Settings** to change any stock in the list to your favorite NSE stock!

---

## Setting Up Alerts on TradingView Free Plan

On TradingView's Free Plan, you can create free alerts for Inside Bar formations or Breakouts:

1. Click the **Alerts** icon (clock icon) on the right sidebar.
2. Click **Create Alert**.
3. Under **Condition**, select **`Inside Bar Screener & Indicator [NSE Daily/Weekly]`**.
4. Select one of the alert conditions:
   - *Bullish Inside Bar Formed*
   - *Bearish Inside Bar Formed*
   - *Bullish Inside Bar Breakout*
   - *Bearish Inside Bar Breakdown*
5. Click **Create**.

---

## Best Practices for NSE Trading
1. **Focus on Daily & Weekly Timeframes**: As noted in PriceAction.com's guide, lower timeframes (5m, 15m) generate noise and false breakouts. Daily & Weekly timeframes give clean, high-conviction trades.
2. **Respect the Trend**: Only take bullish breakouts when price is above the 50 EMA, and bearish breakdowns when price is below the 50 EMA.
3. **Manage Risk**: Always use 1-2% risk per trade and stick to a minimum Risk:Reward ratio of 1:2.
