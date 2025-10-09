# ITUS_Stock_retriever
# 📈 ITUS Capital – Stock Price Retriever

This project dynamically retrieves **historical stock closing prices** from a local SQLite database (`prices.db`) and updates them in a **Google Sheet** in real time.
It was built as part of the **ITUS Capital Data Analyst Intern Technical Assessment**.

---

## 🚀 Overview

The script connects:

* A **SQLite database** containing stock price data.
* A **Google Sheet** (via Google API Service Account credentials).

When the user enters:

* A **ticker symbol** in cell `A1` (e.g., `ITC.NS`)
* A **date** in cell `A2` (format: `YYYY-MM-DD`)

→ The program automatically fetches the **closing price** and displays it in cell `A4`.

---

## 🧩 Features

✅ Real-time update when A1 or A2 changes
✅ Retrieves price directly from SQLite (`prices` table)
✅ Finds **nearest date** if an exact match doesn’t exist
✅ **Color-coded output**:

* 🟢 Green → exact match
* 🔵 Blue → nearest date match
* 🔴 Red → error or invalid input
  ✅ Two operation modes:

1. **Auto-Update Mode** (live monitoring)
2. **Test Mode** (single query from terminal)

✅ Error handling for:

* Missing or invalid dates
* Database or Google API connection errors
  ✅ Professional console logs and structured flow

---

## 🧠 Tech Stack

| Component                        | Description                         |
| -------------------------------- | ----------------------------------- |
| **Python**                       | Core programming language           |
| **SQLite3**                      | Local database engine               |
| **gspread**                      | Google Sheets API client            |
| **Google OAuth Service Account** | Secure authentication               |
| **Pandas**                       | (Optional) for previewing DB tables |

---

## 🗂️ File Structure

```
project/
│
├── prices.db                  # SQLite database (with stock prices)
├── stocksqlite-xxxxxx.json    # Google API credentials (private)
├── stock_price_retriever.py   # Main script
├── .gitignore                 # Ignore credentials & checkpoints
└── README.md                  # This file
```

---

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/itus-stock-price-retriever.git
cd itus-stock-price-retriever
```

### 2. Install dependencies

```bash
pip install gspread pandas google-auth
```

### 3. Place required files

* Ensure `prices.db` and your service account JSON (e.g., `stocksqlite-xxxx.json`) are in the same directory.
* Make sure `.gitignore` excludes the credentials file:

  ```
  *.json
  ```

### 4. Share your Google Sheet

* Open your target Google Sheet.
* Share it with your service account email (found inside the JSON file).
  Example: `your-service-account@project-id.iam.gserviceaccount.com`

---

## ▶️ Running the Script

### Option 1 – Auto-Update Mode

Automatically monitors cells and updates A4 when inputs change:

```bash
python stock_price_retriever.py
```

Then select option **1** when prompted.

### Option 2 – Test Mode

Test a single ticker and date manually:

```bash
python stock_price_retriever.py
```

Then select option **2**.

---

## 📊 Example Workflow

| Cell   | Input / Output | Example      |
| ------ | -------------- | ------------ |
| **A1** | Ticker         | `ITC.NS`     |
| **A2** | Date           | `2010-01-04` |
| **A4** | Closing Price  | `₹184.32`    |

If the date doesn’t exist, it’ll show the nearest available:

```
₹184.32 (nearest: 2010-01-05)
```

---

**© 2025 ITUS Capital Technical Assessment Project**
