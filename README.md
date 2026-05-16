# Shadowbroker

A powerful trading bot and market analysis tool built with Python.

[![CI](https://github.com/your-org/shadowbroker/actions/workflows/ci.yml/badge.svg)](https://github.com/your-org/shadowbroker/actions/workflows/ci.yml)
[![Docker](https://github.com/your-org/shadowbroker/actions/workflows/docker-publish.yml/badge.svg)](https://github.com/your-org/shadowbroker/actions/workflows/docker-publish.yml)

## Overview

Shadowbroker is a fork of [BigBodyCobain/Shadowbroker](https://github.com/BigBodyCobain/Shadowbroker), extended with additional features, improved reliability, and Docker support.

> **Personal fork note:** I'm using this primarily for paper trading and learning purposes. Not running this with real funds.

## Features

- Automated market analysis and trading signals
- Configurable strategy engine
- Docker-ready deployment
- Comprehensive CI/CD pipeline
- Environment-based configuration

## Requirements

- Python 3.11+
- Docker & Docker Compose (optional)
- See `.env.example` for required environment variables

## Getting Started

### Local Development

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-org/shadowbroker.git
   cd shadowbroker
   ```

2. **Set up environment variables**

   ```bash
   cp .env.example .env
   # Edit .env with your credentials and configuration
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Run the bot**

   ```bash
   python main.py
   ```

### Docker

1. **Build and run with Docker Compose**

   ```bash
   docker compose up --build
   ```

2. **Run in detached mode**

   ```bash
   docker compose up -d
   ```

## Configuration

All configuration is handled via environment variables. Copy `.env.example` to `.env` and fill in the required values.

| Variable | Description | Required |
|---|---|---|
| `API_KEY` | Exchange API key | Yes |
| `API_SECRET` | Exchange API secret | Yes |
| `LOG_LEVEL` | Logging verbosity (`DEBUG`, `INFO`, `WARNING`, `ERROR`) | No |
| `PAPER_TRADING` | Set to `true` to run in paper trading mode (no real orders) | No |
| `DRY_RUN_NOTIFY` | Set to `true` to print a reminder on startup that paper trading is active | No |
| `POLL_INTERVAL_SECONDS` | How often (in seconds) the bot checks for new signals (default: `60`) | No |

See `.env.example` for the full list of available options.

> **Tip:** I default `LOG_LEVEL` to `DEBUG` locally so I can follow along with what the bot is doing. I also always keep `PAPER_TRADING=true` — easy safeguard against accidentally placing real orders. I added `DRY_RUN_NOTIFY=true` for the same reason; it prints a visible reminder in the logs at startup so there's no ambiguity about which mode is active. I also set `POLL_INTERVAL_SECONDS=30` locally so signals feel more responsive while I'm actively watching — the upstream default of 60 is fine for unattended runs.

## Development

### Pre-commit Hooks

This project uses [pre-commit](https://pre-commit.com/) for code quality checks.

```bash
pip install pre-commit
pre-commit install
```

### Running Tests

```bash
pytest tests/
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feat/my-feature`)
3. Commit your changes following [Conventional Comm