# dr-manhattan

**CCXT-style unified API for prediction markets.**  
Simple, scalable, and easy to extend.

[![](https://deepwiki.com/badge.svg)](https://deepwiki.com/guzus/dr-manhattan)

<p align="center">
  <img src="assets/polymarket.png" alt="Polymarket" width="50"/>
  <img src="assets/kalshi.jpeg" alt="Kalshi" width="50"/>
  <img src="assets/opinion.jpg" alt="Opinion" width="50"/>
  <img src="assets/limitless.jpg" alt="Limitless" width="50"/>
  <img src="assets/predict_fun.jpg" alt="Predict.fun" width="50"/>
</p>

## What is dr-manhattan?

`dr-manhattan` is a unified Python library that lets you interact with multiple prediction market platforms using the **same simple code**.

It works similarly to **CCXT** for crypto exchanges. You can fetch markets, place orders, check balances, and more — all with consistent methods across different platforms.

---

## Quick Start

### 1. Installation

```bash
# Create a virtual environment
uv venv

# Install the package in editable mode
uv pip install -e .
```

### 2. Basic Usage (No login required)

```python
import dr_manhattan

# Initialize exchanges
polymarket = dr_manhattan.Polymarket({'timeout': 30})
opinion = dr_manhattan.Opinion({'timeout': 30})

# Fetch markets
markets = polymarket.fetch_markets()

# Print first few markets
for market in markets[:5]:
    print(f"Question: {market.question}")
    print(f"Prices : {market.prices}\n")
```

---

## Key Features

- Unified interface for multiple prediction markets
- Support for Polymarket, Opinion, Limitless, Predict.fun, and more
- Place & cancel orders
- Check positions and balances
- Real-time WebSocket support
- Strategy base class for building bots
- **MCP Server** – Trade directly from Claude Desktop / Claude Code

---

## Advanced Usage (With Authentication)

```python
# Example: Polymarket
polymarket = dr_manhattan.Polymarket({
    'private_key': 'your_private_key_here',
    'funder': 'your_funder_address',
})
```

> **⚠️ Security Note:** Never hardcode or commit your private keys. Use environment variables or `.env` files.

---

## MCP Server (Trade using Claude)

You can connect this library directly to Claude:

```bash
# Install with MCP support
uv sync --extra mcp

# Copy environment file
cp .env.example .env
```

Then configure Claude Desktop or Claude Code using the settings shown in the MCP section.

---

## Project Structure

```bash
dr_manhattan/
├── base/           # Core abstractions and base classes
├── exchanges/      # Support for each platform
├── models/         # Data models (Market, Order, Position...)
├── strategies/     # Ready-to-use strategy templates
└── utils/          # Helper functions
```

---

## Examples

Check the [`examples/`](examples/) folder:

- `list_all_markets.py` — List markets from any exchange
- `spread_strategy.py` — Simple market making strategy

Run an example:

```bash
uv run python examples/list_all_markets.py polymarket
```

---

## Contributing with Claude

This project is designed to work with **Claude Code**.  
Just open an issue, describe what you want, and mention `@claude`.

---

## Requirements

- Python >= 3.11
- Recommended: [`uv`](https://docs.astral.sh/uv/) package manager

---

**Ready to get started?** Try the Quick Start above!
