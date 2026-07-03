# MT5-Python-Execution-Bridge

# Enterprise Python-to-MetaTrader 5 Algorithmic Execution Bridge

A robust, production-ready infrastructure shell for connecting Python-based quantitative trading strategies directly to the MetaTrader 5 terminal. 

This repository provides the core operational pipeline required to transform theoretical mathematical signals into live broker execution. It acts as an institutional boilerplate, removing the complexity of broker integration while enforcing strict risk parameters.

## Core Engineering Features

* **Network Fault Tolerance (The Blast Shield):** Features a global exception-handling loop that insulates the core engine from terminal drops, broker lag, or internet stutters, automatically re-initiating synchronization without manual script restarts.
* **Dynamic Capital Allocation:** Includes a precision lot-sizing calculator that parses raw account balances, contract tick values, instrument tick sizes, and broker step limits to risk an exact percentage per trade.
* **Automated Filling Mode Detection:** Queries the broker's underlying specifications dynamically on every execution request to apply the correct filling flag (`ORDER_FILLING_FOK`, `ORDER_FILLING_IOC`, or `ORDER_FILLING_RETURN`), eliminating immediate order rejections.
* **Server-Synchronized Engine Cycles:** Monitors the broker's server-side clock to detect new candle finalizations instead of relying on inaccurate local system times.

## Getting Started

1. Open your MetaTrader 5 Terminal. Ensure "Algo Trading" is enabled in the top toolbar.
2. Install dependencies:
   ```bash
   pip install MetaTrader5 pandas numpy
