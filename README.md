# ETL Data Pipeline with Airbyte, Snowflake, and dbt

This project demonstrates the creation of a modern ELT (Extract, Load, Transform) pipeline using **Airbyte**, **Snowflake**, and **dbt**, culminating in analysis of trading data for profit evaluation. This work is done as a part of CS639 - Data Nanagement in Data Science course at UW Madison. 

Note: This project was completed and submitted as part of a course two months ago via GitHub Classroom (private repo). The current repository reflects a single upload for portfolio purposes, not the original commit history.

---

## Project Overview

The pipeline handles:

- Extraction and loading of survey data from Google Sheets via Airbyte 
- Ingestion of trading and weights data (CSV files) via Airbyte
- Integration of external data from the Snowflake Marketplace (stock and FX prices)
- Transformation of raw data into structured staging models and fact tables using dbt
- Analytical queries on trading profits using Snowflake SQL
---

##  Tools & Stack

- **Airbyte (Cloud)**: Data extraction from external sources and ingestion into Snowflake
- **Snowflake**: Cloud data warehouse for scalable storage and computation
- **dbt**: SQL-based transformation layer to define staging and mart models
- **Matplotlib**: Used for survey dataset visualizations
- **Jupyter Notebook**: To orchestrate configuration, SQL queries, and visualizations

---

## Key Components

**Data Sources**
- Classroom Survey data (Google Sheets: https://docs.google.com/spreadsheets/d/1EOykPOCrZB_l0wNlPSDpIC_JAWBRHRNofPJKyyooxV8/edit?gid=1807517008#gid=1807517008)
- Trading data (`trading_books.csv`, `weights_table.csv` from https://github.com/Snowflake-Labs/sfguide-deploying-pipelines-with-snowflake-and-dbt-labs/tree/main/dbt_project/seeds)
- Snowflake Marketplace data (Forex Tracking: Currency Exchange Rates by Day and Stock Tracking: US Stock Prices by Day datasets)

**Staging Models in dbt**  
*(Shown via `!cat` in `etl_pipeline_airbyte_dbt_snowflake.ipynb`)*
- `staging_valid_stock_tickers.sql`
- `staging_valid_fx_info.sql`
- `staging_buy_sell_joint.sql`

**Mart Table**
- `fact_tab_trading.sql`: Computes trade-level profits (buy, sell, profit)

**Generated Output Files (CSV)**

| File Name                         | Description |
|----------------------------------|-------------|
| `staging_valid_stock_tickers.csv` | Filtered valid stock tickers from trading data |
| `staging_valid_fx_tickers.csv`    | Filtered valid FX tickers from trading data |
| `staging_valid_stock_info.csv`    | Stock price data joined from marketplace |
| `staging_valid_fx_info.csv`       | FX rate data joined from marketplace |
| `staging_buy_sell_joint.csv`      | Combined buy/sell trade records with computed values |
| `fact_tab_trading.csv`            | Final table with profit per trade, grouped by desk |

---

**Analysis**
- Total profit grouped by desk (`Equity`, `FX`)
- Profit rate per desk
- Executed and explained in `etl_pipeline_airbyte_dbt_snowflake.ipynb` using Snowflake SQL

---

## File Structure

```bash
.
├── etl_pipeline_airbyte_dbt_snowflake.ipynb  # Main notebook with commands, SQL, and analysis
├── files/
│   ├── fact_tab_trading.csv
│   ├── staging_valid_fx_tickers.csv
│   ├── staging_valid_stock_tickers.csv
│   ├── staging_valid_stock_info.csv
│   ├── staging_valid_fx_info.csv
│   └── staging_buy_sell_joint.csv
├── Report.pdf                      # Final project write-up with screenshots and details
├── README.md                       # This file
