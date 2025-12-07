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
main/
 * [Data](smart-building-energy-forecasting/Data)
   * [energydata_complete.csv](smart-building-energy-forecasting/Data/energydata_complete.csv)
 * [sql](smart-building-energy-forecasting/sql)
   * [smart_city.db](smart-building-energy-forecasting/sql/smart_city.db)
 * [notebooks](Smart_city_optimization.ipynb/notebooks)
   * [ Smart_city_optimization.ipynb](Smart_city_optimization.ipynb/notebooks/Smart_city_optimization.ipynb)
 * [notebooks](Project Documentation.ipynb/notebooks)
   * [Project Documentation.ipynb](Project Documentation.ipynb/notebooks/Project Documentation.ipynb)
 * [dashboard](smart-building-energy-forecasting/dashboard)
   * [smart_city_resource_optimization.pbix](smart-building-energy-forecasting/dashboard/smart_city_resource_optimization.pbix)
    * [README.md](Urban_mobility_analysis/README.md)


## Data
Source: UCI Machine Learning Repository
Dataset: Appliances Energy Prediction Data Set
10‑minute resolution measurements from a residential building
Variables used:
date – timestamp
Appliances – appliance energy usage (Wh)
T_out – outside temperature (°C)
RH_out – outside humidity (%)      
