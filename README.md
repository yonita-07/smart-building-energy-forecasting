# Smart Building Energy Forecasting: Behavioral vs Climate Load Drivers

This project analyzes how outdoor weather (temperature, humidity) relates to appliance‑level energy consumption in a residential building. It combines **SQL**, **Python**, and **Power BI** to answer a key smart‑city question: **Can we reliably forecast appliance energy demand using only weather data, and how should cities prioritize optimization efforts?**

## Key Findings

- **Weather explains almost none of the variation in appliance energy**  
  - Daily Energy vs. Temperature correlation = **0.007**  
  - Linear Regression Test **R² = −0.05**, MAE = **23.6 Wh**
- **Conclusion:** Appliance usage is **behavior‑driven, not climate‑driven**.  
  - Forecasting this load type from weather alone is ineffective.
  - Optimization should focus on **occupancy patterns, device scheduling, and behavior**, not just temperature.
    
## Project Structure

 * [Data](Data)
   * [energydata_complete.csv](Data/energydata_complete.csv)
 * [sql](sql)
   * [smart_city.db](sql/smart_city.db)
 * [notebooks](notebooks)
   * [Smart_city_optimization.ipynb](notebooks/Smart_city_optimization.ipynb)
   * [Project_Documentation.ipynb](notebooks/Project_Documentation.ipynb)
 * [dashboard](dashboard)
   * [smart_city_resource_dashboard.pbix](dashboard/smart_city_resource_dashboard.pbix)
   * [smart_city_resource_dashboard.jpg](dashboard/smart_city_resource_dashboard.jpg)
 * [README.md](README.md)

## Technical Skills Demonstrated

- **Languages:** Python (pandas, numpy), SQL (SQLite)
- **Data Handling:** Data cleaning, time-series aggregation (10‑minute → daily → monthly), joining multi-table data
- **Analysis & Statistics:** Exploratory data analysis (EDA), correlation analysis, trend analysis
- **Machine Learning:** Linear Regression (scikit‑learn), train/test split, evaluation with R² and MAE
- **Databases:** SQLite (table design, joins using SQL and Python)
- **Visualization:** Matplotlib / Seaborn (Python), Power BI (KPIs, line charts, tables with conditional formatting)
- **Reporting & Storytelling:** Jupyter Notebooks, formal project report (`REPORT.md`), Power BI dashboard with business insights

## Data

- **Source:** UCI Machine Learning Repository
- **Dataset:** Appliances Energy Prediction Dataset
    - 10‑minute resolution measurements from a residential building
    - Variables used:
      - date – timestamp
      - Appliances – appliance energy usage (Wh)
      - T_out – outside temperature (°C)
      - RH_out – outside humidity (%)

## Logical Data Model

To demonstrate SQL + multi-table modeling, the CSV is split into:
1. energy_consumption
   - date, appliances_energy(from Appliances), optional internal temps
2. weather
   - date, T_out, RH_out, Press_mm_hg, Windspeed
     
Joined on date and stored in SQLite: db/smart_city.db

## Methods

### 1.SQL & Data Modeling
- Created energy_consumption and weather tables in SQLite.
- Performed INNER JOIN on Timestamp
- Used this joined data as the base for analysis in Python.

### 2. Feature Engineering (Python)
- Aggregated 10-minute data to **daily** level:
  - avg_daily_energy (Wh)
  - avg_daily_temp (°C)
  - avg_daily_humidity (%)
- Built **monthly** aggregates for trend analysis

### 3. Exploratory Data Analysis
- **Daily scatter:** Energy vs Temperature
- **Monthly trend:** Average daily energy by month
- **Correlation heatmap:** avg_daily_energy, avg_daily_temp, avg_daily_humidity

Key EDA insight: visually and statistically, **no strong relationship** between daily energy and weather variables.

### 4. Predictive Modelling
- **Model:** Linear Regression (scikit-learn)
- **Features:** avg_daily_temp, avg_daily_humidity
- **Target:** avg_daily_energy
- **Metrics:** Train/ Test split, R-squared, MAE

**Results:**
- Train R-Squared = 0.015
- Test R-Squared = -0.051
- Test MAE = 23.6 Wh
Model performs worse than predicting the mean that shows **weather-only model is not useful** for this load.

## Power BI Dashboard
The Power BI dashboard (dashboard/smart_city_resource_dashboard.pbix) summarizes:
- **KPI Cards:**
    - ML Test R-Squared (Low Predictive Power)
    - Average Prediction Error (Wh)
    - Energy- Temperature Correlation (Weak)
- **Monthly Energy Trend**
     - Line chart of average daily energy by month
- **High-Use Day Analysis**
     - Matrix/ table of top high-energy days with conditional formatting

## What This Project Demonstrates
- **SQL & Data Modelling**
  - Designing logical tables from a flat IoT dataset
  - Joining multiple tables on timestamp
- **Python Data Science**
  - Aggregations (daily/monthly), EDA, correlation analysis
  - Building and evaluating an ML regression model
- **BI & Storytelling**
  - Translating technical results into KPIs and visuals for non‑technical stakeholders
  - Communicating that no relationship is itself an important finding

## Future Work
- Add calendar and occupancy features (weekday/weekend, holidays).
- Separate appliance vs. HVAC loads and model them independently.
- Experiment with non‑linear models (Random Forest, Gradient Boosting).
- Deploy an interactive dashboard via Streamlit or a web app.

## Related Projects
My portfolio focuses on data-driven sustainability and smart city optimization:
- [retail-sustainability-analytics](https://github.com/yonita-07/retail-sustainability-analysis.git) – Power BI dashboard for waste and emission reduction
- [urban-mobility-forecasting](https://github.com/yonita-07/urban-mobility-analysis.git) – Python + ML model for public transit demand prediction
- [smart-city-energy-optimization](https://github.com/yonita-07/smart-building-energy-forecasting.git) – This project
