# Retail Sales Customer Segmentation Dashboard

A data analysis project that transforms raw online retail data into actionable business insights through SQL-based data cleaning, RFM customer segmentation, and an interactive Power BI dashboard.

---

## Project Highlights

- **5,835 customers** segmented across **78 unique RFM scores**
- **3.45M+** in total revenue analyzed
- Purchase recency ranging from **23 to 761 days**
- Customer frequency spanning **1 to 10,700+ transactions**
- Interactive Power BI dashboard with year, month, and country filters

---

## Dataset

The dataset is sourced from [Kaggle - Online Retail Data v3](https://www.kaggle.com/datasets/coldperformer/online-retail-data-v3) and contains the following fields:

| Column | Description |
|--------|-------------|
| `Bill` | Invoice identifier |
| `MerchandiseID` | Product identifier |
| `Product` | Product name |
| `Quota` | Quantity ordered |
| `BillDate` | Invoice date |
| `Amount` | Transaction amount |
| `CustomerID` | Customer identifier |
| `Country` | Customer country |

---

## Workflow

### 1. Data Cleaning (SQL)

Raw data was cleaned and standardized using SQL Server:

- **Type formatting** — Converted `BillDate` to a proper `DATE` type.
- **Null removal** — Deleted rows with missing `Bill`, `MerchandiseID`, or `CustomerID` values.
- **Deduplication** — Identified and removed redundant records using `ROW_NUMBER()` with partitioning across all columns.
- **Column renaming** — Renamed `Quota` → `Quantity` for clarity and rounded `Amount` to two decimal places.

### 2. RFM Analysis (SQL)

Customers were scored on three dimensions using `NTILE(5)` grouping:

- **Recency** — Days since the customer's last purchase (relative to 2020-01-01).
- **Frequency** — Total number of transactions per customer.
- **Monetary** — Total spend per customer.

Each dimension is scored 1–5, producing a composite RFM score (e.g., `555` = highest value customer, `111` = lowest). The analysis identified **513 top-tier customers** (score `555`) and **432 at-risk customers** (score `111`).

### 3. Power BI Dashboard

An interactive dashboard was built with the following visuals:

- Quantity orders vs. invoice date (trend line)
- Total sales vs. invoice date (trend line)
- Highest sold product
- Country-level total and average revenue table
- Most valuable customer by RFM score
- Monthly total and average revenue breakdown
- Customer count per RFM segment
- Filters for year, month, and country

---

## Project Files

```
├── RetailData.xlsx                  # Raw dataset from Kaggle
├── Cleansed_RetailData.csv          # Cleaned output data
├── RFM_RetailData_Analysis.csv      # RFM scores for all 5,835 customers
├── Cleansed_RetailData_Script.sql   # SQL cleaning & RFM script
├── Retail_Analysis_Report.pbix      # Power BI dashboard
└── README.md                        # This file
```

---

## Getting Started

1. **Review the SQL script** — Open `Cleansed_RetailData_Script.sql` to see the full cleaning and RFM logic.
2. **Explore the RFM data** — Open `RFM_RetailData_Analysis.csv` to browse customer segments.
3. **Open the dashboard** — Load `Retail_Analysis_Report.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) to interact with the visuals and apply filters.

---

## Tools Used

- **SQL Server** — Data cleaning and RFM analysis
- **Power BI** — Dashboard and visualizations
- **Excel / CSV** — Data storage and export

