## Overview

This project delivers a comprehensive analytics dashboard built in **Tableau** that explores the intersection of climate change, CO₂ emissions, and economic consequences. It tracks data across **8 countries** (Australia, Brazil, Canada, Germany, India, South Africa, USA, and China), spanning multiple decades from historical emission records (as far back as 1751) to modern climate measurements (2024–2026).

The dashboard is designed for environmental researchers, policy analysts, and data enthusiasts who want to explore:
- How CO₂ emissions have evolved by country over time
- The economic toll of extreme weather events by season
- Correlations between temperature and air quality
- Year-over-year emission change trends

---

## Key Metrics

| Metric | Value |
|---|---|
| 🌡️ Avg. Temperature | **17.45 °C** |
| 💨 Avg. Air Quality Index | **255.6** |
| 💰 Total Economic Impact | **$50M** |
| 🏭 Total CO₂ Emissions (2021) | **240,689** |
| ⛈️ Extreme Weather Events Recorded | **15,351** |

---

## Dashboard Visualizations

### 1. 📊 Economic Impact by Season × Weather Event
A cross-tabulation heatmap showing the percentage economic impact distribution across four seasons (Autumn, Spring, Summer, Winter) and four extreme weather types (Drought, Flood, Heatwave, Hurricane).

- **Winter Droughts** carry the highest economic share at **27.39%**
- **Autumn Droughts** are the least impactful at **22.02%**
- All season rows sum to **100%**, enabling easy relative comparison

### 2. 🔵 Temperature vs Air Quality Index (Scatter Plot)
Visualizes the relationship between recorded temperature (°C) and Air Quality Index (AQI) values. The scatter reveals:
- AQI values span a wide range (~0–450) across all temperature bands
- No strong linear correlation — air quality is influenced by multiple factors beyond temperature alone

### 3. 🌐 CO₂ by Country & Year (Heatmap Table)
A color-encoded matrix of CO₂ emissions per country from **2007 to 2021**. Key observations:
- **China** dominates with values exceeding **9,956** units (displayed as `####` where columns overflow)
- **India** shows consistent growth: 2,384 → 2,626 → 2,710 across recent years
- Most Western nations show relatively stable or declining trends

### 4. 📈 Economic Impact Trend by Month (Line Chart)
Tracks average monthly economic impact from **2024 to 2026** across all countries. The multi-line chart shows:
- Volatile fluctuations between ~$40M and ~$60M monthly
- No single country consistently dominates economic losses

### 5. 🎯 Bullet Chart — CO₂ Emissions 2021 vs 2020
Compares 2021 CO₂ emissions (bar) against 2020 baseline (reference line) for each country. This highlights year-over-year changes and whether countries increased or reduced their carbon footprint post-pandemic.

### 6. 📉 Emission Change Timeline by Country
A diverging bar chart showing emission growth or decline over time per country. Color-coded by **Trend Type**:
- 🔴 **Increase** — countries with rising emissions
- 🔷 **Decrease** — countries showing improvement

---

## Dataset Description

### `Climate_Change_Data.csv`
The primary dataset containing **15,353 records** of daily climate observations across cities and countries.

| Column | Description |
|---|---|
| `Record ID` | Unique record identifier (e.g., `aus_1`) |
| `Date` | Observation date (MM/DD/YYYY) |
| `Country` | Country name |
| `City` | City of measurement |
| `Temperature` | Ambient temperature in °C |
| `Humidity` | Relative humidity (%) |
| `Precipitation` | Rainfall in mm |
| `Air Quality Index` | AQI value (higher = worse air quality) |
| `Extreme Weather Events` | Type of event (Flood, Drought, Hurricane, etc.) or None |
| `Climate Classification` | Köppen climate classification (A, B, C, D) |
| `Climate Zone` | Broad zone (Arid, Tropical, etc.) |
| `Biome Type` | Ecosystem type (Forest, Wetland, Desert, Grassland, Tundra) |
| `Heat Index` | Perceived temperature accounting for humidity |
| `Wind Speed` | Wind speed (km/h or mph) |
| `Wind Direction` | Cardinal direction (N, S, E, W, NE, etc.) |
| `Season` | Season of observation (Summer, Winter, Spring, Autumn) |
| `Population Exposure` | Estimated population exposed to the weather event |
| `Economic Impact Estimate` | Estimated economic damage in USD |
| `Infrastructure Vulnerability Score` | Score 1–10 indicating infrastructure risk |

**Countries covered:** Australia, Brazil, Canada, China, Germany, India, South Africa, USA

---

### `emission_data.csv`
Historical CO₂ emission data spanning from **1751 to 2017**, covering **230+ countries and regions**.

| Column | Description |
|---|---|
| `Country` | Country or region name |
| `1751–2017` | Annual CO₂ emissions (metric tonnes of carbon) |

Notable entities include country-level data (Afghanistan → Zimbabwe), continental aggregates (Africa, Americas), and a **World** total row for global benchmarking.

---

## Project Structure

```
📦 climate-change-analytics/
├── 📊 Climate_Change_Impact_and_Co2_Emission_Analytics.twbx   # Tableau packaged workbook
├── 📄 Climate_Change_Data.csv                                  # Primary climate dataset (15K+ rows)
├── 📄 emission_data.csv                                        # Historical CO₂ emissions (1751–2017)
├── 🖼️ Dashboard_1.png                                          # Dashboard screenshot
└── 📝 README.md                                                # Project documentation
```

---

## Getting Started

### Prerequisites
- [Tableau Desktop](https://www.tableau.com/products/desktop) (version 2022.1 or later recommended) **or**
- [Tableau Public](https://public.tableau.com/) (free)

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/climate-change-analytics.git
   cd climate-change-analytics
   ```

2. **Open the Tableau workbook**
   - Launch Tableau Desktop or Tableau Public
   - Open `Climate_Change_Impact_and_Co2_Emission_Analytics.twbx`
   - The `.twbx` format is self-contained — data is embedded, no additional setup required

3. **Explore the dashboard**
   - Use the **Country** filter (top right) to isolate specific nations
   - Adjust the **Economic Impact** and **CO₂** color legend sliders to focus on ranges of interest
   - Click any chart element to cross-filter related visualizations

4. **Working with raw data (optional)**
   - Both `.csv` files can be opened in Excel, Python (pandas), or R for custom analysis
   ```python
   import pandas as pd

   climate_df = pd.read_csv("Climate_Change_Data.csv")
   emission_df = pd.read_csv("emission_data.csv")

   print(climate_df.shape)    # (15353, 19)
   print(emission_df.shape)   # (230, 268)
   ```

---

## Insights & Findings

- **China's Dominance:** China's CO₂ output dwarfs all other tracked nations, with figures nearly 4× that of the next largest emitter (India) in recent years.
- **Winter Extremes Cost More:** Economic losses from weather events peak in Winter, particularly from droughts, suggesting cold-season agricultural and infrastructure vulnerability.
- **Air Quality Is Multi-Causal:** The temperature vs AQI scatter shows no simple linear relationship — AQI is driven by industrial activity, seasonality, and geography, not just heat.
- **Post-Pandemic Emission Rebound:** The 2021 vs 2020 bullet chart reveals that most countries saw emission increases in 2021, consistent with global economic recovery trends post-COVID.
- **India's Rapid Growth:** India shows the steepest upward trend in the emission change timeline, reflecting its continued industrial and economic development.

---

## Tools & Technologies

| Tool | Purpose |
|---|---|
| **Tableau Desktop / Public** | Dashboard creation and interactive visualization |
| **CSV (Excel-compatible)** | Data storage and portability |
| **Köppen Climate System** | Standard climate classification scheme |
| **Historical Emission Records** | Long-term trend context (1751–2017) |

---

## Contributing

Contributions are welcome! If you'd like to extend this project:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/new-analysis`)
3. Commit your changes (`git commit -m 'Add regional breakdown view'`)
4. Push to your branch (`git push origin feature/new-analysis`)
5. Open a Pull Request

Ideas for extension:
- Add per-capita emission normalization
- Integrate population data for exposure-adjusted analysis
- Build a Python/Streamlit version of the dashboard
- Add forecasting using ARIMA or Prophet models
