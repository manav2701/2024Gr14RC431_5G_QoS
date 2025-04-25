# 5G Quality of Service (QoS) Analysis 


## 2024Gr14RC431_5G_QoS
*Group Details:*
- Smit Shah - 202251122
- Heet Shah - 202251121
- Manav Mehta - 202252344
- Jhanvi Mehta - 202252322


## Overview
5G is the next-generation mobile network technology that promises significantly higher data rates, ultra-low latency, massive device connectivity, and enhanced reliability compared to its predecessors. These characteristics enable transformative applications such as real-time video conferencing, autonomous vehicles, remote surgery, and massive Internet-of-Things (IoT) deployments. Ensuring *Quality of Service (QoS)* in a 5G network is critical to unlocking these use cases and meeting Service-Level Agreements (SLAs) between network providers and end users.

This repository demonstrates a data-driven workflow to:
1. *Load & preprocess* raw 5G QoS measurements.
2. *Compute key metrics*: signal strength, latency, bandwidth utilization, jitter, and SLA compliance.
3. *Perform statistical tests* (ANOVA) and *correlation analysis* to understand relationships among metrics.
4. *Visualize* distributions and dependencies across different application types.
5. *Export* results and figures for reporting and further study.

---

## Project Structure

5G/
├── Quality_of_Service_5G.csv      # Raw CSV Main dataset
├── 2024Gr14RC431_5G_QoS.ipynb     # Colab notebook with full analysis
└── results/                       # Outputs directory
    ├── anova_results.txt
    ├── data_info.txt
    ├── feature_correlation_heatmap.png
    ├── feature_correlation_matrix.csv
    ├── first_rows.csv
    ├── latency_by_app.png
    ├── signal_strength_by_app.png
    ├── resource_allocation_by_app.png
    └── summary_statistics.csv  


---

## Data Preprocessing
1. *Parse timestamps* and set a DateTime index for time-series operations.
2. *Extract numeric values* from string fields:
   - Signal Strength (dBm)
   - Latency (ms)
   - Required & Allocated Bandwidth (Mbps)
   - Resource Allocation (%)
3. *Standardize* (Z-score) signal strength and latency to compare different scales.
4. *Compute derived metrics*:
   - *Bandwidth Utilization Ratio* = Allocated / Required
   - *Jitter (ms)* = Rolling standard deviation of latency (per user)
   - *SLA Compliance* = (Latency ≤ threshold) AND (Utilization ≥ 1.0)

---

## Statistical Analysis
- *ANOVA* to test whether resource allocation (%) differs significantly by Application_Type.
- *Correlation matrix* (Pearson) to quantify linear relationships among standardized signal, latency, raw bandwidths, utilization ratio, and allocation.

---

## Visualization
- *Boxplots*: Show distributions of standardized signal, latency, and resource allocation by application type, with distinct colors per category.
- *Heatmap*: Correlation matrix annotated for easy interpretation.

All plots are saved at *300 dpi* under the results/ folder for high-definition use in reports.

---

## Key Findings (Sample)
- *Signal vs. Latency*: Moderate negative correlation (r ≈ –0.45) indicating stronger signal generally yields lower latency.
- *Bandwidth Utilization*: Applications with high utilization ratio often exhibit increased jitter, affecting real‑time performance.
- *ANOVA*: Significant difference in resource allocation across application types (F > 5, p < 0.01).

---

## Next Steps
- Extend time-series decomposition on longer datasets to uncover diurnal patterns.
- Build predictive models for SLA breaches using early-session metrics.
- Apply clustering to segment users by QoS profiles for targeted optimizations.

---
