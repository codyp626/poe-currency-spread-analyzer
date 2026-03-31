# PoE Spread Analyzer

A real-time currency spread analyzer for Path of Exile's Mirage league. Finds the most profitable currency flipping opportunities by analyzing bid/ask spreads from [poeez.com](https://poeez.com).

## Features

- **Live Data**: Pulls from the poeez.com API and auto-refreshes every hour
- **Spread Analysis**: Shows buy/sell prices and profit spread for every tradeable currency item
- **Cross-Currency Arbitrage**: Detects opportunities to buy items with chaos orbs and sell for divine orbs at a profit
- **Sortable**: Sort by total profit (chaos value), percentage profit, or trade volume
- **Filterable**: Filter by currency type (chaos/divine), search by item name, set minimum volume thresholds
- **Summary Cards**: At-a-glance view of the best opportunities across categories

## How It Works

### Spread Calculation
The API returns bid/ask ratios. For items worth multiple orbs (ratio < 1), the per-item price is `1 / ratio`. For bulk currencies (ratio ≥ 1), the ratio represents how many items per orb.

- **Buy Price**: What it costs you to acquire 1 item (from the bid ratio)
- **Sell Price**: What you receive selling 1 item (from the ask ratio)
- **Spread**: Sell Price − Buy Price = your profit per flip

### Cross-Currency Arbitrage
Finds items where buying with chaos and selling for divines yields profit after converting divines back to chaos value. Example: buy 10 scarabs for 250c total, sell 9 scarabs for 1 divine, and divines are worth 290c = 40c profit.

## Deployment

This is a single static HTML file — no build step required.

### GitHub Pages
1. Push this repo to GitHub
2. Go to Settings → Pages
3. Set source to "Deploy from a branch" → `main` / `/ (root)`
4. Your site will be live at `https://<username>.github.io/<repo-name>/`

### Local
Just open `index.html` in a browser.

## Data Source

All data comes from [poeez.com](https://poeez.com/api/Economy/pc/Mirage). The endpoint is the Mirage league on PC. To change leagues, modify the `API_URL` constant at the top of the script section.

## License

MIT
