# XAUIDR Trading Dashboard

Real-time monitoring dashboard for XAUIDR Phase 1 manual scalp trading.

## Features

- 📊 **Live P&L Tracking** - Daily and total profit/loss
- 📈 **Win Rate Monitor** - Current vs target (56%)
- 📋 **Trade History** - Detailed trade log with entry/exit prices
- 🔔 **Alert Status** - Webhook connectivity and last signal
- 📊 **Backtest Comparison** - Historical vs live performance
- 🎨 **Dark Theme** - Easy on the eyes
- 📱 **Responsive** - Works on desktop and mobile
- ⚡ **Real-time Updates** - Auto-refresh every 30 seconds

## Metrics Displayed

- **Daily P&L**: Profit/loss for today
- **Win Rate**: Percentage of winning trades (target: 56%)
- **Total P&L**: 30-day cumulative profit
- **Max Drawdown**: Peak-to-trough decline (target: <5%)
- **Sharpe Ratio**: Risk-adjusted return metric
- **Last Alert**: Time of last TradingView signal

## Data Source

Dashboard reads from `~/trading-tools/trade_log.json` which is auto-populated by:
1. TradingView webhook alerts
2. Manual trade logging via webhook receiver
3. Daily cron summary (22:00 IDT)

## Deployment

### GitHub Pages (Recommended)

1. Push to GitHub:
```bash
cd ~/xauidr-trading-dashboard
git add .
git commit -m "Initial dashboard setup"
git remote add origin https://github.com/wisnuputra17/xauidr-trading-dashboard.git
git branch -M main
git push -u origin main
```

2. Enable GitHub Pages:
   - Go to: https://github.com/wisnuputra17/xauidr-trading-dashboard
   - Settings → Pages
   - Source: main branch
   - Save

3. Dashboard live at: `https://wisnuputra17.github.io/xauidr-trading-dashboard/`

## Local Development

Open `index.html` in browser:
```bash
open index.html
```

Or serve locally:
```bash
python3 -m http.server 8000
# Visit: http://localhost:8000
```

## Data Integration

To connect with real trade data:

1. Export `trade_log.json` from trading-tools:
```bash
cp ~/trading-tools/trade_log.json ./data/trades.json
```

2. Update JavaScript in `index.html` to fetch:
```javascript
fetch('./data/trades.json')
  .then(r => r.json())
  .then(data => {
    mockTrades = data;
    updateDashboard();
  });
```

3. Auto-sync via GitHub Actions (coming soon):
   - Daily cron to pull latest trade data
   - Auto-commit and push updates

## Features Roadmap

- [ ] Connect to live trade_log.json
- [ ] Real-time WebSocket updates
- [ ] Strategy variant comparison
- [ ] Performance charts (P&L over time)
- [ ] Risk metrics dashboard
- [ ] Export reports (PDF)
- [ ] Mobile app version
- [ ] Alerts for target metrics

## Phase 1 Goals

- Win Rate: ≥56%
- Profit Factor: ≥1.7x
- Max Drawdown: <5%
- Minimum Trades: 30+

## Support

Dashboard updates automatically every 30 seconds. For manual refresh, reload browser.

---

Built for XAUIDR Phase 1 Trading Validation (2026-09-20)
