# **Enterprise Python-to-MetaTrader 5 Algorithmic Execution Bridge**

A robust, production-ready infrastructure shell for connecting Python-based quantitative trading strategies directly to the MetaTrader 5 terminal.  
This repository provides the core operational pipeline required to transform theoretical mathematical signals into live broker execution. It acts as an institutional boilerplate, removing the complexity of broker integration while enforcing strict risk parameters.

## **Core Engineering Features**

* **Network Fault Tolerance (The Blast Shield):** Features a global exception-handling loop that insulates the core engine from terminal drops, broker lag, or internet stutters, automatically re-initiating synchronization without manual script restarts.  
* **Dynamic Capital Allocation:** Includes a precision lot-sizing calculator that parses raw account balances, contract tick values, instrument tick sizes, and broker step limits to risk an exact percentage per trade.  
* **Automated Filling Mode Detection:** Queries the broker's underlying specifications dynamically on every execution request to apply the correct filling flag (ORDER\_FILLING\_FOK, ORDER\_FILLING\_IOC, or ORDER\_FILLING\_RETURN), eliminating immediate order rejections.  
* **Server-Synchronized Engine Cycles:** Monitors the broker's server-side clock to detect new candle finalizations instead of relying on inaccurate local system times.

## **Prerequisites**

Before deploying this infrastructure, ensure your environment meets the following requirements:

* **Operating System:** Windows (The official MetaTrader5 Python library is exclusively compiled for Windows).  
* **Python:** Version 3.8 or higher.  
* **Terminal:** MetaTrader 5 installed and logged into an active brokerage account (Demo or Live).

## **Getting Started**

1. Open your MetaTrader 5 Terminal. Ensure the **"Algo Trading"** button is enabled (green) in the top toolbar.  
2. Install the required Python dependencies:  
   pip install MetaTrader5 pandas numpy

3. Open execution\_engine.py and configure your global variables at the top of the file:  
   SYMBOL \= "XAUUSDm"            \# Match your broker's exact ticker  
   TIMEFRAME \= mt5.TIMEFRAME\_H1  \# Base operation interval  
   RISK\_PERCENT \= 0.01           \# 1% risk per trade

4. Run the engine wrapper:  
   python execution\_engine.py

## **Injecting Your Strategy (The Alpha Matrix)**

This boilerplate is strictly an execution shell. By design, all proprietary mathematical formulas, machine learning models, and entry/exit parameters have been scrubbed.  
To deploy your own strategy, locate the generate\_signals(df) function within the script. The engine will automatically pass the latest historical dataframe to this function upon every new candle close.  
Write your custom logic inside this block and return the required tuple format: (signal\_code, trade\_context, log\_message).

## **Legal Disclaimer**

**This software is for educational and research purposes only.**  
Trading foreign exchange on margin carries a high level of risk and may not be suitable for all investors. The past performance of any trading system or methodology is not necessarily indicative of future results. By using this software, you acknowledge that you are using it at your own risk. The author assumes absolutely no responsibility or liability for any financial losses, account blowouts, or software malfunctions resulting from the use of this code in a live market environment.

## **License**

This project is licensed under the MIT License. You are free to use, modify, and distribute this software within your own proprietary systems.