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
 * [README.md](README.md)


## Data
Source: UCI Machine Learning Repository
Dataset: Appliances Energy Prediction Data Set
10‑minute resolution measurements from a residential building
Variables used:
date – timestamp
Appliances – appliance energy usage (Wh)
T_out – outside temperature (°C)
RH_out – outside humidity (%)      
