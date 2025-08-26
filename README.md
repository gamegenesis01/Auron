# AuronTrader

<img src="docs/images/auron_logo.png" alt="Auron Logo" width="120"/>

---

## Introduction
**AuronTrader** is a high-performance, production-grade algorithmic trading platform designed for quantitative traders.

It lets you:
- **Backtest** portfolios of automated trading strategies on historical data.
- **Deploy live** with no code changes, keeping research and production in sync.
- **Scale across markets** including equities, futures, FX, and crypto.

## Why Auron?
- **AI-First** – Python-native APIs designed to integrate with AI/ML strategies.
- **Parity** – Research/backtest and live trading share the same strategy code.
- **Performance** – Rust-powered core dependencies (via upstream libraries) for ultra-low latency.

## Features
- ⚡ **Fast** – async event processing; sub-ms performance targets.
- 🛡️ **Reliable** – type-safe, thread-safe components for mission-critical trading.
- 🖥️ **Portable** – Linux, macOS, Windows. Docker-ready.
- 🔌 **Flexible** – modular adapters for REST/WebSocket data feeds and brokers.
- 🎯 **Advanced** – support for advanced order types (IOC, FOK, GTC, GTD, AT_OPEN, AT_CLOSE, Reduce-Only, Icebergs).
- 📊 **Universal** – equities, FX, futures, crypto, prediction markets.

## Architecture
![Auron Architecture](docs/images/auron_architecture.png)

**Core Components**
- **Data Engine** → Ingests tick, order book and kline/bar data (CSV, Parquet, live APIs).
- **Strategy Engine** → Runs AI/quant models in Python with nanosecond timestamps.
- **Execution Engine** → Broker/exchange connectors with risk gating.
- **Risk Engine** → Position sizing, exposure limits, SL/TP, drawdown controls.
- **MessageBus** → High-throughput event distribution across components.

## Integrations
Planned adapters:
- **Market Data:** Databento, Polygon, Tardis.
- **Execution Venues:** Interactive Brokers, Binance, Coinbase, OKX, Bybit.
- **Persistence:** Parquet catalogs (PyArrow), optional Redis cache.

## Platform Support

| Platform         | Rust  | Python     | Status |
|------------------|-------|------------|--------|
| Linux (x86_64)   | 1.89+ | 3.11–3.13  | ✅ |
| Linux (ARM64)    | 1.89+ | 3.11–3.13  | ✅ |
| macOS (ARM64)    | 1.89+ | 3.11–3.13  | ✅ |
| Windows (x86_64) | 1.89+ | 3.11–3.13  | ✅ |

## Quick Start

```bash
# Clone
git clone https://github.com/auronlabs/auron-trader.git
cd auron-trader

# Install (using uv)
pip install uv
uv sync

# Run a sample backtest (no external deps required)
auron run --config configs/backtest.yaml

# Or test Discord notifications
auron notify --discord-webhook https://example.com/webhook --message "Auron is live"
