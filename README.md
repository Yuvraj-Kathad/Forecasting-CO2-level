# Forecasting CO₂ Levels

**Project:** Forecasting CO₂ Level at Mauna Loa Observatory

## 📄 Abstract

This repository contains a comprehensive time‑series forecasting project on atmospheric CO₂ concentrations recorded monthly at Mauna Loa, Hawaii (1958–present). We clean and interpolate the raw data, conduct stationarity tests, and compare a suite of statistical and deep‑learning models, including:

* **Naive methods (Naive, Seasonal Naive, Mean, Seasonal Mean)**
* **Classical time‑series models (AR, MA, ARMA, ARIMA, SARIMA)**
* **Deep learning architectures (LSTM, RNN, GRU)**

Forecast performance is evaluated using MAE, RMSE, and MAPE. Our findings demonstrate the trade‑off between interpretability (SARIMA) and predictive power (LSTM, GRU), and provide actionable CO₂ forecasts with uncertainty bounds.

## 📂 Repository Structure

```
├── data/                    # Raw and processed datasets
│   ├── CO2_mm_mlo.txt       # Monthly raw CO₂ measurements
│   └── processed.csv        # Cleaned & interpolated series
├── notebooks/               # Jupyter notebooks
│   ├── 1_data_exploration.ipynb
│   ├── 2_stationarity_tests.ipynb
│   ├── 3_naive_methods.ipynb
│   ├── 4_statistical_models.ipynb
│   └── 5_deep_learning_models.ipynb
├── src/                     # Python scripts / modules
│   ├── data_utils.py        # Data loading & preprocessing
│   ├── stats_models.py      # AR, MA, ARMA, ARIMA, SARIMA implementations
│   └── dl_models.py         # LSTM, RNN, GRU model definitions
├── results/                 # Plots and performance metrics
│   ├── figures/             # PNG or interactive HTML plots
│   └── metrics.csv          # Summary of RMSE / MAPE comparisons
├── requirements.txt         # Python dependencies
└── README.md                # Project overview (this file)
```

## ⚙️ Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/<your-username>/forecasting-co2.git
   cd forecasting-co2
   ```
2. **Create a virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Linux/macOS
   venv\\Scripts\\activate  # Windows
   ```
3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

## 🗄️ Dataset

* Source: NOAA’s Global Monitoring Laboratory ‒ Mauna Loa CO₂ monthly dataset.
* Fields include calendar year/month, decimal-year timestamp, raw & deseasonalized CO₂, valid count, daily standard deviation, and uncertainty.
* Missing values flagged by negative codes (e.g., -99.99) are cleaned via interpolation.

## 📈 Methodology

1. **Data Exploration & Visualization**

   * Plot raw CO₂ trends and seasonal cycles.
2. **Stationarity Analysis**

   * Augmented Dickey‑Fuller (ADF) tests before/after first differencing.
3. **Baseline Naive Methods**

   * Naive, Seasonal Naive, Mean, Seasonal Mean forecasts.
4. **Statistical Models**

   * AR(p), MA(q), ARMA(p,q), ARIMA(p,d,q), and SARIMA(p,d,q)(P,D,Q)
5. **Deep Learning Models**

   * Multivariate LSTM, RNN, and GRU architectures leveraging features like monthly mean, deseasonalized value, count, standard deviation, and uncertainty.

## 📊 Results & Observations

* **Naive Methods:** Seasonal Naive improved over simple Naive (RMSE ≈20 vs. 22).
* **Classical Models:** SARIMA (1,1,1)x(2,1,3)¹12 achieved RMSE ≈4.17, MAPE ≈0.85%.
* **Deep Learning:** LSTM (RMSE ≈1.95, MAPE ≈0.38%) outperformed GRU and RNN, though at higher computational cost.
* **Key Trade‑off:** Interpretability of SARIMA vs. predictive accuracy of gated RNNs.

## 🔍 Key Learnings

* Importance of stationarity checks (ADF tests, differencing).
* Value of seasonal differencing for annual cycles.
* Model selection via AIC and forecast metrics (MAE, RMSE, MAPE).
* Balanced workflow: start from naive baselines → classical → deep learning.

## 🚀 Usage

To reproduce the results:

```bash
# 1. Explore data and test stationarity
jupyter notebook notebooks/1_data_exploration.ipynb
jupyter notebook notebooks/2_stationarity_tests.ipynb

# 2. Run forecasting methods
jupyter notebook notebooks/3_naive_methods.ipynb
jupyter notebook notebooks/4_statistical_models.ipynb
jupyter notebook notebooks/5_deep_learning_models.ipynb
```

Or execute scripts in `src/`:

```bash
python src/data_utils.py
python src/stats_models.py
python src/dl_models.py
```

## 👥 Contributors

* **Yuvraj Kathad** (202203013) *
---

*Happy forecasting!*
