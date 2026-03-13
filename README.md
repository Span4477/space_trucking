# Space Trucking - Eve Online Market Analysis

[![Python 3.14.2](https://img.shields.io/badge/python-3.14.2-blue.svg)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

**Space Trucking** is an Eve Online market analysis tool for finding arbitrage opportunities and optimizing trading routes across the stars.

![Eve Online Trading](https://img.shields.io/badge/Eve_Online-Market_Analysis-purple?style=flat-square)

---

## 📖 About

Space Trucking helps identify profitable trading routes by:

- 📥 Downloading market order data from Eve Online
- 💰 Calculating buy/sell spreads between stations and systems
- 🗺️ Computing shortest paths between solar systems via stargates
- 📊 Ranking trade opportunities by profit and margin

### Key Features

| Feature | Description |
|---------|-------------|
| **Arbitrage** | Find price differences between stations |
| **Routing** | Calculate optimal paths through stargates |
| **Profit Analysis** | Compute ROI, profit per jump |
| **Filtering** | Filter by margin, volume, profitability |

---

## 🛠 Technologies

- **Python 3.14.2**
- **Jupyter Notebooks** — interactive analysis
- **Libraries**:
  - `pandas` — data manipulation
  - `numpy` — numerical operations
  - `networkx` — graph algorithms
  - `matplotlib` — visualization
  - `requests` — data downloading
  - `scikit-learn`, `prophet` — forecasting (available)

---

## 📦 Installation

### Requirements

- Python 3.14.2 or compatible version
- pip for package management

### Quick Start

```bash
# Clone the repository
git clone <repository-url>
cd space_trucking

# Create and activate virtual environment
python -m venv .venv
source .venv/bin/activate  # macOS/Linux
# or
.venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt
```

### Running Jupyter

```bash
# With venv activated
jupyter notebook
# or
jupyter lab
```

---

## 🚀 Usage

### 1. Download Data (`get_data.ipynb`)

The first notebook downloads and prepares data:

- Fetches market history, orders, and reference data from everef.net
- Filters data for **"The Forge"** region (region_id: 10000002)
- Saves processed DataFrames as pickle files for fast loading

### 2. Analyze Market (`analyze_market_orders.ipynb`)

The second notebook performs analysis:

- Loads preprocessed data from pickle files
- Builds stargate graph for route calculation
- Identifies arbitrage opportunities (buy low → sell high)
- Calculates profit margins and optimal routes

---

## 📊 Analysis Metrics

Arbitrage analysis calculates:

| Metric | Formula | Description |
|--------|---------|-------------|
| **Spread** | `price_buy - price_sell` | Price difference |
| **Spread %** | `(spread / price_sell) * 100` | Percentage margin |
| **Max Units** | — | Max quantity (limited by cargo volume) |
| **Total Profit** | `spread * max_units / 1e6` | Profit in million ISK |
| **Jumps** | — | Shortest path via stargates |
| **Profit/Jump** | `total_profit / jumps` | Profit per jump |

### Filtering Criteria

Trade opportunities are filtered by:

- ✅ Spread > 0
- ✅ Spread % > 10%
- ✅ Total Profit > 25 million ISK
- ✅ Item volume < 5737 m³ (MAX_VOLUME)

---

## 📁 Project Structure

```
space_trucking/
├── get_data.ipynb              # Data download and preprocessing
├── analyze_market_orders.ipynb # Market analysis and arbitrage
├── requirements.txt            # Python dependencies
├── README.md                   # This file
├── LICENSE                     # License
├── data/                       # Data (git-ignored)
│   ├── *.csv.bz2              # Compressed market data
│   ├── *.pkl                  # Pickle DataFrames
│   ├── *.json                 # Structure data
│   └── *.jsonl                # Static data
└── .venv/                      # Virtual environment
```

---

## 🌐 Data Sources

The project uses data from official Eve Online sources:

| Source | URL |
|--------|-----|
| Market History | https://data.everef.net/market-history/ |
| Market Orders | https://data.everef.net/market-orders/ |
| Reference Data | https://data.everef.net/reference-data/ |
| Structures | https://data.everef.net/structures/ |
| Industry Facilities | https://data.everef.net/industry-facilities/ |
| EVE Static Data | https://developers.eveonline.com/static-data/ |

---

## ⚠️ Notes

- **Default Region**: The Forge (10000002)
- **Pochven**: Handled via filament-based travel
- **Caching**: Data is saved to `data/` for reuse
- **Download Time**: Initial data download may take significant time

---

## 💰 Support

If you find this project helpful, consider supporting:

- **Eve Online**: Send ISK to character **Span Matsutake**
- **GitHub**: ⭐ Star the repository

---

## 📄 License

See the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

This is a community-created project for Eve Online players interested in market trading. Pull requests and issues are welcome!

---

*Space Trucking — find the best routes, maximize your profits!* 🚀
