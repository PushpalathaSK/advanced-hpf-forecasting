# Advanced Hierarchical Probabilistic Forecasting (HPF)

This repository contains the full implementation for the **Advanced Time Series Forecasting with Hierarchical Probabilistic Modeling** project.  
The project includes synthetic hierarchical data generation, baseline modeling, aggregation, reconciliation, evaluation, and final forecast outputs.

---

## 📘 Project Overview

This project focuses on forecasting demand across a **three-level hierarchy**:

- **Level 0 (Total)** – Overall sales  
- **Level 1 (Region)** – 5 regions  
- **Level 2 (Store)** – 20 stores per region (100 stores total)

A **3-year daily dataset** is programmatically generated with:

- Weekly seasonality
- Annual seasonality
- Noise
- Promotion spikes
- Store-specific trend + level differences

The goal is to produce:

- Probabilistic forecasts
- Forecast coherence across levels
- Comparison of baseline vs. hierarchical methods

---

## 🧪 Modeling Approach

### 1️⃣ **Baseline Model: ETS (Holt–Winters)**
- An ETS model with weekly seasonality was fitted to each of the 100 store-level series.
- 90-day forecasts were generated for each store.
- Prediction intervals were computed from residual standard errors.

### 2️⃣ **Aggregation (Bottom-Up)**
Store-level forecasts were summed to:

- Region-level forecasts
- Total forecast

### 3️⃣ **Aggregate Models (Region + Total ETS)**
Separate ETS models were fitted directly to:

- Each of the 5 region totals  
- The overall total series  

### 4️⃣ **Reconciliation**
Final region + total forecasts were obtained by:

Reconciled Forecast = 0.5 * Bottom-Up + 0.5 * ETS Aggregate



This simple averaging provides coherence while keeping computational cost low.

---

## 📊 Evaluation Metrics

Simple baselines were evaluated on a 90-day holdout:

- **MASE** (Mean Absolute Scaled Error)  
- **wMAPE** (Weighted Mean Absolute Percentage Error)

Metrics for Region + Total are saved in:


---


