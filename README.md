# Stellar High-Frequency Trading (HFT) Triangular Arbitrage  Bot

## Overview
The Stellar High-Frequency Trading (HFT) Bot is a modular and dynamic application designed to execute a **strict triangular arbitrage strategy** on the Stellar network. The bot identifies profitable arbitrage paths among multiple asset pairs, ensures reserve requirements are met, and executes trades efficiently while handling market conditions and liquidity constraints in real-time.

## Features
- **Triangular Arbitrage**: Identifies and executes profitable arbitrage opportunities across three asset pairs.
- **Dynamic Asset Management**: Ensures trades comply with target allocations and reserve requirements for all assets.
- **Robust Rebalancing Logic**: Automatically rebalances assets to maintain predefined target allocations.
- **Real-Time Execution**: Processes trades immediately upon detecting arbitrage opportunities.
- **Logging and Reporting**: Detailed logging of transactions and arbitrage opportunities, with support for Excel logging.
- **Configurable Parameters**: Parameters like profit thresholds, slippage, transaction fees, and time buffers are customizable via `config.ini`.

## Project Structure
```
├── agr_bar_assets.py        # Generates asset bar graphs and HTML reports.
├── agr_idx_assets.py        # Creates asset snapshots and index values.
├── arbitrage_utils.py       # Utility functions for fetching exchange rates, order books, and validating reserves.
├── config.ini               # Configuration file for customizable parameters.
├── excel_logger.py          # Logs arbitrage opportunities and results into Excel.
├── main.py                  # Entry point for the bot, manages the workflow and transaction queue.
├── trade_assetlist.py       # Contains the list of tradable assets with their configurations.
├── triangular_arbitrage.py  # Core logic for finding and executing triangular arbitrage.
├── utils.py                 # Shared utilities for logging, configuration management, and calculations.
├── etf_assetlist.py         # Defines ETF asset allocations and dynamic asset management.
```

## Configuration
The `config.ini` file contains all configurable parameters:
- **Stellar Network**:
  - `horizonurl`: The URL of the Stellar Horizon server.
  - `networkpassphrase`: The passphrase for the Stellar network.
- **Account Settings**:
  - `account_id`: The Stellar account ID.
  - `secretkey`: The secret key for signing transactions.
- **Arbitrage Settings**:
  - `profit_threshold`: Minimum profit percentage for executing a trade.
  - `slippagepercent`: Factor for calculating slippage in trades.
- **Transaction Settings**:
  - `basefee`: Base transaction fee in stroops.
  - `defaultsendamount_min` & `defaultsendamount_max`: Range for the amount sent in arbitrage trades.
  - `timebuffer_min` & `timebuffer_max`: Time bounds for transactions.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/stellar-hft-bot.git
   cd stellar-hft-bot
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Configure the `config.ini` file with your Stellar account details and trading preferences.

## Usage
1. Start the bot by running:
   ```bash
   python3 main.py
   ```
2. The bot will:
   - Continuously monitor the Stellar network for arbitrage opportunities.
   - Log transactions and rebalancing activities in real-time.
   - Generate visual reports for asset allocations and balances.

## Key Functions
### **Triangular Arbitrage**
Located in `triangular_arbitrage.py`, this module:
- Scans enabled assets for profitable arbitrage paths.
- Validates reserves and liquidity before executing trades.
- Ensures that all trades comply with target allocations.

### **Asset Rebalancing**
Rebalancing logic in `triangular_arbitrage.py`:
- Adjusts asset allocations to match predefined targets.
- Prevents trades involving over-allocated or under-allocated assets.

### **Logging and Reporting**
- Logs arbitrage opportunities in detail.
- Creates interactive HTML reports and Excel logs for tracking performance.

## Dependencies
- **Python Libraries**:
  - `stellar_sdk`
  - `pandas`
  - `matplotlib`
  - `plotly`
  - `openpyxl`
- **Stellar Horizon**:
  - Ensure access to a reliable Stellar Horizon server.

## Troubleshooting
1. **Transaction Failures**:
   - Ensure sufficient XLM balance for fees.
   - Validate the `dest_min` calculation to avoid order failures.
2. **Configuration Issues**:
   - Double-check values in `config.ini`.
   - Ensure `AssetReserves` in `config.ini` matches your strategy.
3. **Logging Errors**:
   - Enable Excel logging by setting `enable_excel_logging = True` in `config.ini`.

## Future Enhancements
- Add support for additional arbitrage strategies.
- Integrate advanced risk management modules.
- Expand asset rebalancing to include dynamic risk scoring.

## License
This project is licensed under the GNU GPLv3 License. See `LICENSE` for details.

## Contributing
Contributions are welcome! Please submit a pull request or open an issue to suggest changes or report bugs.

---
**Contact:** For questions or support, please reach out to the repository maintainer or submit an issue on GitHub.

