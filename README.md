# Uber NYC Pickup Demand and Hotspot Analytics  

This project analyzes NYC Uber pickup demand using TLC/FiveThirtyEight Uber pickup records to understand **when** riders request trips, **which bases dominate demand**, and **where pickup hotspots persist over time**.  
It combines exploratory analysis, an explanatory **time-effects regression**, and **K-means spatial clustering** to produce interpretable demand insights and hotspot maps.

---

## Project Overview

The notebook studies pickup demand from three angles:  
(1) **base-level operations** (concentration and trends), (2) **temporal dynamics** (weekday/weekend mix, intraday rhythms, seasonality), and (3) **spatial structure** (stable hotspots and their evolution over time).  
Because the data is **pickup-only**, the analysis focuses on demand patterns rather than trip outcomes (no fares, dropoffs, distances, or durations).

---

## Key Steps

1. **Data Preparation**
   - Load and clean Uber pickup records (date/time, base ID, latitude/longitude; 2014–2015).
   - Engineer time features (date, hour, day-of-week, month).
   - Build aggregated views (daily counts, hourly profiles, base-level panels).

2. **Exploratory Data Analysis (EDA)**
   - Base-level pickup volume, ranking, and demand concentration.
   - Weekday vs. weekend composition by base.
   - Intraday patterns (hourly curves by day-of-week).
   - Monthly seasonality and trend signals.

3. **Explanatory Modeling**
   - Fit an OLS regression with weekday and month dummies to quantify time drivers of daily pickup volume.
   - Compare coefficient patterns against EDA results and review model fit/diagnostics.

4. **Spatial Clustering and Hotspot Mapping**
   - Run K-means on pickup coordinates with a K sweep (≈6–7) to choose an interpretable segmentation.
   - Visualize hotspot centroids on Folium maps and interpret cluster geography.
   - Track month-over-month hotspot dynamics (centroid movement + pickup share shifts).

---

## Insights

- Pickup demand is highly concentrated across a small number of bases; weekday commuter activity dominates overall volume (~75%).  
- Intraday demand shows a consistent structure: overnight trough, morning ramp, and a sustained late-day peak (16:00–21:00) aligned with evening commute behavior.  
- Time effects explain most variance in daily pickups (R² ~0.76); Mondays/Sundays are materially below Friday, while summer months deliver the largest lift.  
- Hotspots remain compact and interpretable at K≈6–7, anchored in Manhattan with recurring airport and outer-borough satellite nodes.

---

## Limitations

- Pickup-only data: no dropoffs, trip distance/duration, fares, wait/cancel metrics, supply conditions, weather/holiday signals, or taxi competition context.  
- As a result, OD flows, pricing/revenue effects, and service-level performance conclusions are out of scope.

---

## Next Steps

- Join pickups to TLC taxi zones and GIS layers for richer spatial summaries and borough-level reporting.  
- Add weather + holiday/event features and re-estimate models with controls/interactions.  
- Compare against NYC taxi demand to test substitution/complementarity using panel or diff-in-diff designs.  
- If the goal is causal impact, define a credible identification strategy (natural experiments or controlled tests) before making “effect” claims.
