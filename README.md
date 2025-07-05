# ETL Data Pipeline with Airbyte, Snowflake, and dbt

This project demonstrates the creation of a modern ELT (Extract, Load, Transform) pipeline using **Airbyte**, **Snowflake**, and **dbt**, culminating in analysis of trading data for profit evaluation. This work is done as a part of CS639 - Data Nanagement in Data Science course at UW Madison. 

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
- Survey data (Google Sheets)
- Trading data (`trading_books.csv`, `weights_table.csv`)
- Public marketplace data (US stock metrics, FX rates)

**Staging Models in dbt**  
*(Shown via `!cat` in `etl_pipeline_airbyte_dbt_snowflake.ipynb`)*
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

## File Structure

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
