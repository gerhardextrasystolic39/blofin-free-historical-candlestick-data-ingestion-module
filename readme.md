# 📊 Blofin Free Historical Candle Data Downloader (Python)

Easily **fetch free historical candlestick (OHLCV) data** from the **Blofin Exchange API** using this simple Python script.  
No API keys required — download years of data for any symbol and interval (1m, 1H, 1D, etc.) and save it directly to a CSV file.

---

## 🚀 Features

✅ 100% **Free** — No API key or authentication  
✅ **Supports all intervals**: 1m, 5m, 15m, 1H, 4H, 1D, 1W  
✅ Fetch **large date ranges** automatically (e.g., 2021–2025)  
✅ Works for any **Blofin trading pair** (e.g., ETH-USDT, BTC-USDT)  
✅ **Auto pagination** with rate-limit safety (0.2s delay)  
✅ Automatically **appends or creates CSVs**  
✅ Ready-to-use **OHLCV + Quote Volume** data  

---

## 🧩 Example Use Cases

- Trading bot **backtesting & research**  
- **Machine learning models** for price prediction  
- **Quantitative analysis** on market structure and volatility  
- Generating historical datasets for **charting tools or dashboards**

---

## 📦 Installation

Make sure you have **Python 3.8+** installed.

Clone the repository and install dependencies:

```bash
git clone https://github.com/frostyalce000/blofin-free-historical-candlestick-data-fetcher.git
cd blofin-free-historical-candlestick-data-fetcher
pip install -r requirements.txt
````

Or manually install the two required libraries:

```bash
pip install requests pandas
```

---

## ⚙️ Configuration

Edit these values inside the script before running:

```python
SYMBOL = "ETH-USDT"              # Trading pair, e.g., BTC-USDT
INTERVAL = "1H"                  # Supported: 1m, 5m, 15m, 1H, 4H, 1D, etc.
START_DATE = "2021-07-16T00:00:00Z"
END_DATE = "2025-10-16T23:59:00Z"
```

The script will automatically fetch candles between those two timestamps and store them in:

```
historical_ETH-USDT_1H_2021-07-16_2025-10-16.csv
```

---

## ▶️ Usage

Run the script:

```bash
python blofin_fetcher.py
```

Example console output:

```
Fetching candles from 2021-07-16 00:00:00+00:00 to 2025-10-16 23:59:00+00:00 for ETH-USDT...
Request #1: Fetching candles before 2025-10-16T23:59:00+00:00 ...
  Retrieved: 500 candles; Total so far: 500
Request #2: Fetching candles before 2025-09-26T00:00:00+00:00 ...
  Retrieved: 500 candles; Total so far: 1000
...
Created new data file: historical_ETH-USDT_1H_2021-07-16_2025-10-16.csv with 20000 records
```

If the output file already exists, it will automatically **append only new data**.

---

## 📂 Output Example

| timestamp            | open    | high    | low     | close   | volume  | quote_volume |
| -------------------- | ------- | ------- | ------- | ------- | ------- | ------------ |
| 2021-07-16T00:00:00Z | 2000.45 | 2012.12 | 1998.20 | 2009.11 | 1456.78 | 2923456.23   |
| 2021-07-16T01:00:00Z | 2009.11 | 2015.80 | 2003.22 | 2010.44 | 1265.11 | 2547120.55   |
| ...                  | ...     | ...     | ...     | ...     | ...     | ...          |

---

## 🧠 Notes

* API endpoint used:
  `https://openapi.blofin.com/api/v1/market/candles`
* Script fetches candles **in reverse order** (from end date backwards).
* Each request retrieves **up to 500 candles** per call.
* Works safely under Blofin’s rate limits with a **0.2s delay** per request.
* Timestamp format: **ISO 8601 (UTC)**

---

## 💡 Example: Fetch BTC-USDT Daily Data

Just modify these variables:

```python
SYMBOL = "BTC-USDT"
INTERVAL = "1D"
START_DATE = "2023-01-01T00:00:00Z"
END_DATE = "2023-12-31T23:59:00Z"
```

---

## 🧰 Tech Stack

* **Language:** Python 3
* **Libraries:** requests, pandas
* **Exchange:** Blofin Exchange
* **Output:** CSV (timestamp, open, high, low, close, volume, quote_volume)

---

## 🌟 Contribute

Contributions, issues, and feature requests are welcome!
If you find this project helpful, please ⭐ **star the repository** to support continued updates.
