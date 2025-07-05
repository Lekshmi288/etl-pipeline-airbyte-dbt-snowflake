# 💼 ETL Data Pipeline with Airbyte, Snowflake, and dbt

This project demonstrates the creation of a modern ELT (Extract, Load, Transform) pipeline using **Airbyte**, **Snowflake**, and **dbt**, culminating in analysis of trading data for profit evaluation.

---

## 🚀 Project Overview

- Extract data from:
  - Google Sheets (survey data)
  - GitHub-hosted CSVs (`trading_books.csv`, `weights_table.csv`)
  - Snowflake Marketplace (US stock and FX datasets)

- Load data into **Snowflake** using **Airbyte**

- Transform data using **dbt**, with SQL files shown inline via `!cat` in `etl_pipeline_airbyte_dbt_snowflake.ipynb`

- Analyze processed data to evaluate trading performance by desk

---

## 🧱 Tools & Stack

- **Airbyte**: Data extraction and loading
- **Snowflake**: Cloud data warehouse
- **dbt**: Data transformation and modeling
- **Python / Jupyter Notebook**: Final queries, outputs, and plots
- **SQL**: Data processing and analysis

---

## 📊 Key Components

**Data Sources**
- Survey data (Google Sheets)
- Trading data (`trading_books.csv`, `weights_table.csv`)
- Public marketplace data (US stock metrics, FX rates)

**Staging Models in dbt**  
*(Shown via `!cat` in `p4.ipynb`)*
- `staging_valid_stock_tickers.sql`
- `staging_valid_fx_info.sql`
- `staging_buy_sell_joint.sql`

**Mart Table**
- `fact_tab_trading.sql`: Computes trade-level profits (buy, sell, profit)

**Generated Output Files (CSV)**
- `staging_valid_fx_tickers.csv`
- `staging_valid_stock_tickers.csv`
- `staging_valid_stock_info.csv`
- `staging_valid_fx_info.csv`
- `staging_buy_sell_joint.csv`
- `fact_tab_trading.csv`

**Analysis**
- Total profit grouped by desk (`Equity`, `FX`)
- Profit rate per desk
- Executed and explained in `p4.ipynb` using Snowflake SQL

---

## 📝 File Structure

```bash
.
├── etl_pipeline_airbyte_dbt_snowflake.ipynb                        # Main notebook with commands, SQL, and analysis
├── files/
│   ├── fact_tab_trading.csv
│   ├── staging_valid_fx_tickers.csv
│   ├── staging_valid_stock_tickers.csv
│   ├── staging_valid_stock_info.csv
│   ├── staging_valid_fx_info.csv
│   └── staging_buy_sell_joint.csv
├── Report.pdf                      # Final project write-up with screenshots and details
├── README.md                       # This file
