# Binance Futures Trading Bot

A trading bot designed for automated futures trading on Binance exchange.

## Features

- Automated futures trading
- Risk management
- Multiple trading strategies
- Real-time market data analysis

## Installation

1. Clone the repository
2. Install dependencies: `pip install -r requirements.txt`
3. Configure your API keys in the config file
4. Run the bot: `python run_bot.py`

## Usage

The bot executes trades based on configured strategies and market conditions.

## Warning

This software is for educational purposes. Test thoroughly before using with real funds.

# Binance Future Trading Bot (EMA Crossover Strategy)
<p>This bot automates future trading on Binance based on Exponential Moving Average (EMA) crossovers. When the short-term EMA crosses above the long-term EMA, it's an indication of upward momentum, and the bot places a buy order. Conversely, when the short-term EMA crosses below the long-term EMA, signaling potential downward momentum, the bot places a sell order.</p>

<b>How It Works:</b>
    <p>In a continuous loop, the bot fetches the latest price for the given symbol and calculates the short and long EMAs.</p>
    <b>Buy Order Logic:</b>
    <p>If the short EMA is greater than the long EMA (indicating potential upward price movement) and the last action wasn't a buy, the bot closes any existing sell order and places a buy order.
        After placing the buy order, the bot checks if the order was fully executed (FILLED status) before updating its last action.</p>
    <b>Sell Order Logic:</b>
    <p>If the short EMA is less than the long EMA (indicating potential downward price movement) and the last action wasn't a sell, the bot closes any existing buy order and places a sell order.
        After placing the sell order, it checks if the order was fully executed before updating its last action.</p>
    <b>Exception Handling:</b> 
    <p>If there's a timeout when communicating with Binance's API, the bot catches the exception and continues operation, ensuring the script doesn't terminate unexpectedly.</p>

# Usage
This bot is executed from the command line and requires the trading pair symbol, data-fetching interval, and the periods for the short and long EMAs as arguments. The bot then continually checks the EMA values and makes decisions based on the crossover strategy.

# Requirments
- Python3.x
- Pip

# Installation
<b>TA-Lib Installation</b>
<pre>
sudo apt-get update
sudo apt-get install build-essential wget
wget http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz
tar -xzf ta-lib-0.4.0-src.tar.gz
cd ta-lib/
./configure --prefix=/usr
make
sudo make install
</pre>

<b>Finally Run</b>
<pre>pip install python-binance requests ta-lib numpy</pre>

# Run
python run_bot.py &lt;Symbol> &lt;Short EMA Period> &lt;Long EMA Period> &lt;Interval> &lt;Leverage> &lt;order size>

<b>Example:</b>
<code>python run_bot.py BTCUSDT 9 30 1h 10 2.5</code>

<b>To Run in Background</b>
<code>nohup python run_bot.py BTCUSDT 9 30 1h 10 2.5 &</code>

<hr>
<b>The Above script was only tested on Ubuntu 20.04.4 LTS Distribution</b>

# Risk Warning
Remember, while the EMA crossover strategy is popular, it's essential to combine it with other indicators or methods for more robust trading signals. Always ensure you are comfortable with the risks before running any trading bot live.
