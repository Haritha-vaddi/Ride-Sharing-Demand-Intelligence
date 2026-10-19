
# Ride-Sharing Demand & Revenue Intelligence

### NYC Yellow Taxi Trip Data | August 2026

**An end-to-end data analytics project using Python, DuckDB SQL, Machine Learning, and Power BI.**

---

## 📥 Official Dataset — Start Here

**Source:** New York City Taxi & Limousine Commission (NYC TLC)

- **[Official NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)**
- **[Download August 2026 Yellow Taxi Dataset (Parquet)](https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2026-08.parquet)**
- **[Download Taxi Zone Lookup CSV](https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv)**

The original and processed datasets are excluded from GitHub due to their large file sizes.

---

## 📌 Project Overview

This project analyzes **NYC Yellow Taxi trip data (August 2026)** to identify demand patterns, revenue distribution, geographical performance, and hypothetical surge pricing opportunities.

**Project Objectives:**

- Clean and preprocess large-scale taxi trip data.
- Analyze demand and revenue using SQL and Python.
- Identify peak demand hours and revenue-generating locations.
- Simulate percentile-based surge pricing.
- Develop a Linear Regression model for fare prediction.
- Build three interactive Power BI dashboard pages.

---

## 📊 Dataset

| Metric | August 2026 |
|---|---:|
| Original Records | 3,336,716 |
| Cleaned Records | 3,163,242 |
| Cleaned Dataset Columns | 27 |

**Dataset includes:** Pickup/drop-off timestamps, trip distance, fare amount, total amount, tip amount, passenger count, and location IDs.

---

## 🧹 Data Cleaning & Feature Engineering

Using **Python, Pandas, and NumPy**:

- Handled missing values and filtered invalid trip records.
- Examined outliers and unusual trip values.
- Calculated trip duration from pickup and drop-off timestamps.
- Created `pickup_hour`, `pickup_day`, `pickup_weekday`, and `is_weekend`.
- Engineered `revenue_per_mile`, `revenue_per_minute`, and `tip_percentage`.
- Exported the cleaned dataset in Parquet format.

---

## 🔍 Exploratory Data Analysis (SQL + Python)

Used **DuckDB SQL** for aggregation and **Matplotlib/Seaborn** for visualization.

### 📈 Demand & Revenue Analysis

- **Peak demand:** 6 PM — 204,503 trips.
- **Lowest demand:** 4 AM — 30,048 trips.
- **Highest revenue:** 5 PM — $6.11M.
- **Lowest revenue:** 4 AM — $0.98M.
- **Highest revenue per trip:** 5 AM — $33.68.

**Insight:** Peak demand and peak recorded charges occurred at different hours.

### 📅 Weekend vs Weekday

| Metric | Weekday | Weekend |
|---|---:|---:|
| Total Trips | 2.10M | 1.06M |
| Average Fare | $20.84 | $21.71 |
| Average Duration | 17.39 min | 17.64 min |
| Average Tip Ratio | 17% | 14% |

**Insight:** Weekdays contributed more total monthly trips, while weekends recorded slightly higher average fares and trip durations.

### 🗺️ Geographic Insights

- **JFK Airport:** $11.39M — highest pickup-zone revenue.
- **LaGuardia Airport:** $5.84M — second highest.
- **Manhattan:** $70.88M — highest borough-level charges.
- **Queens:** $20.33M — second highest borough.
- **Average charges per trip:** Queens $67.66 vs Manhattan $25.78.

**Insight:** Manhattan dominated overall passenger charges, while airport-related trips contributed significantly to Queens' average trip value.

---

## 🚀 Dynamic Surge Pricing Simulation

Implemented a percentile-based pricing simulation using hourly taxi demand.

| Demand Percentile | Surge Multiplier |
|---|---|
| Below 75th | 1.0× |
| 75th–below 85th | 1.2× |
| 85th–below 95th | 1.5× |
| 95th and above | 2.0× |

### Simulation Results

| Metric | Value |
|---|---:|
| Original Passenger Charges | $95.42M |
| Simulated Passenger Charges | $116.53M |
| Hypothetical Revenue Uplift | **22.12%** |

**Insight:** The simulation produced a 22.12% hypothetical uplift under unchanged-demand assumptions.

*Note: This is a simulated pricing scenario, not observed revenue growth or a validated business forecast.*

---

## 🤖 Machine Learning — Fare Prediction

**Algorithm:** Linear Regression (Scikit-learn)

**Input Features:**
- `trip_distance`
- `trip_duration_min`

**Target:** `fare_amount`

**Train-Test Split:** 80% training, 20% testing.

### Model Performance

| Metric | Result |
|---|---:|
| R² Score | **0.193** |
| Mean Absolute Error | **$9.55** |
| Test Records | 632,649 |

**Insight:** The baseline model explained approximately 19.3% of fare variation, indicating opportunities for further feature engineering and model improvement.

Because actual trip duration is an input, the model estimates completed-trip fares rather than providing advance fare quotes.

---

## 📊 Power BI Dashboards

Developed a **three-page Power BI report** using DAX measures and interactive visualizations.

### Dashboard 1 — NYC Taxi Demand, Revenue & Surge Analysis

**KPI Cards:**
- Total Trips: **3.16M**
- Total Revenue: **$95.42M**
- Average Fare: **$21.13**
- Revenue Uplift: **22.12%**

**Visualizations:**
- Trips by Hour
- Revenue by Hour

![Dashboard 1 — Demand & Revenue](Dashboard/Dashboard-1.png)

### Dashboard 2 — Location-Based Revenue Intelligence

**Visualizations:**
- Total Revenue by Borough
- Total Trips by Borough
- Revenue by Pickup Zone

**Key Finding:** Manhattan leads in total charges, while JFK Airport ranks first among pickup zones.

![Dashboard 2 — Location Intelligence](Dashboard/Dashboard-2.png)

### Dashboard 3 — Surge Pricing Impact

**KPI Cards:**
- Original Revenue: **$95.42M**
- Simulated Revenue: **$116.53M**
- Hypothetical Uplift: **22.12%**

**Visualization:**
- Original Revenue vs Simulated Revenue by Hour

![Dashboard 3 — Surge Pricing](Dashboard/Dashboard-3.png)

*The complete Power BI `.pbix` report is stored separately due to its file size.*

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Data cleaning and analysis |
| Pandas & NumPy | Data preprocessing |
| DuckDB SQL | Data aggregation and querying |
| Matplotlib & Seaborn | Exploratory visualizations |
| Scikit-learn | Linear Regression |
| Power BI | Interactive dashboards |
| DAX | KPI calculations |
| Parquet & CSV | Data storage |
| Git & GitHub | Version control and portfolio |

---

## 📁 Project Structure

```text
Ride-Sharing-Demand-Intelligence/
├── Dashboard/
│   ├── Dashboard-1.png
│   ├── Dashboard-2.png
│   └── Dashboard-3.png
├── Notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_eda_analysis_using_SQL_&_Python.ipynb
│   └── 03_regression.ipynb
├── Insights/
│   └── insights.md
└── README.md
```

---

## ▶️ How to Reproduce

1. Download the official **August 2026 Yellow Taxi Parquet dataset** and taxi zone lookup CSV using the links above.
2. Install the Python dependencies:

   ```bash
   pip install pandas numpy matplotlib seaborn duckdb scikit-learn pyarrow jupyter
   ```

3. Run the notebooks in order:
   - `01_data_cleaning.ipynb`
   - `02_eda_analysis_using_SQL_&_Python.ipynb`
   - `03_regression.ipynb`
4. Export `final_yellow_tripdata_2026-08.csv` from Notebook 02.
5. Import the final CSV and `taxi_zone_lookup.csv` into Power BI.
6. Create the DAX measures and three dashboard pages.

---

## 💡 Key Takeaway

This project demonstrates an **end-to-end data analytics workflow**, integrating data cleaning, SQL analysis, Python visualization, Machine Learning, and Power BI.

The analysis highlights evening demand peaks, strong airport-related revenue, differences in geographic trip values, and a hypothetical **22.12% surge-pricing uplift**.

The regression baseline also identifies opportunities to improve fare prediction through further modeling and data-quality improvements.

---

**Data Source:** NYC Taxi & Limousine Commission (TLC).

*Independent portfolio project. Not affiliated with NYC TLC.*
