 Weather Forecasting Project

## 📌 Project Overview
This project focuses on weather forecasting using time series models, particularly Facebook Prophet, and anomaly detection using STL + ESD. The dataset includes weather attributes such as temperature, precipitation, wind speed, humidity, and air quality, recorded at 15-minute intervals.

## 🎯 Objectives
- Perform Exploratory Data Analysis (EDA) to understand trends and seasonality.
- Develop a time series forecasting model using Facebook Prophet.
- Detect anomalies in weather features using STL + ESD.
- Evaluate model performance and suggest improvements.

## 📂 Dataset
- **Original Shape:** (60,218, 41)
- **Shape after Outlier Removal:** (25,425, 41)
- **Key Features:** Temperature, Precipitation, Wind Speed, Humidity, Pressure, Air Quality.
- **Time Interval:** 15 minutes, using `last_updated` as the datetime index.

## 🛠 Data Preprocessing
- **Handling Missing Values:**
  - Columns with >40% missing values were removed.
  - Numeric missing values were filled using the median; categorical values with mode.
- **Feature Scaling:** StandardScaler was applied to numerical features.
- **Feature Engineering:** New features such as rolling averages were introduced.

## 🔍 Exploratory Data Analysis (EDA)
- **Seasonality Analysis:** Monthly temperature and precipitation trends were visualized.
- **Geospatial Mapping:** Heatmaps for extreme weather conditions.
- **Correlation Analysis:** Relationships between weather variables were explored.

## 📈 Forecasting Model: Facebook Prophet
### Why Prophet?
- Handles missing values, seasonality, and trend shifts effectively.
- Provides interpretability with additive components.

### Model Training
- **Target Variables:** `precip_in` and `temperature_celsius`
- **Hyperparameter Tuning:** Seasonal effects and holiday components were adjusted.

### Model Evaluation
#### **Precipitation Forecasting:**
- MAE: 0.5466
- RMSE: 0.6936
- MAPE: 340.69%
- R²: 0.3761

#### **Temperature Forecasting:**
- MAE: 0.9612
- RMSE: 1.1167
- MAPE: 397.81%
- R²: -0.0112

### Interpretation
- **Temperature predictions show high volatility**, affecting accuracy.
- **Precipitation models exhibit moderate performance**, but MAPE is high.

## 🚨 Anomaly Detection: STL + ESD
### Methodology
- **STL Decomposition:** Separates trend, seasonal, and residual components.
- **ESD Test:** Identifies extreme outliers in the residual component.

### Findings
- High anomalies detected in `wind_kph`, `pressure_mb`, and `air_quality_PM10`.
- Possible sensor errors affecting `visibility_km` and `cloud` readings.

![Anomaly Detection](https://github.com/user-attachments/assets/d886e819-d392-4944-beac-4c4a3d971077)


## 📌 Key Insights & Recommendations
### 🔹 Key Findings
- Temperature forecasting is **highly volatile**.
- Precipitation forecasting **needs further tuning**.
- Detected anomalies may indicate **sensor errors or extreme weather events**.

### 🔹 Suggested Improvements
- Implement **ensemble models** (ARIMA, SARIMA, XGBoost) for improved forecasting.
- Use **multivariate factors** like humidity and pressure for better accuracy.
- Apply **sensor calibration techniques** to reduce anomalies.

## 🚀 Next Steps
- Experiment with alternative forecasting models.
- Optimize Prophet hyperparameters further.
- Improve data quality and anomaly handling.

## 📜 Repository Structure
```
|-- data/                # Contains dataset files
|-- notebooks/           # Jupyter notebooks for EDA & modeling
|-- src/                 # Python scripts for model training & evaluation
|-- results/             # Forecasting outputs and anomaly reports
|-- README.md            # Project overview and instructions
```

## 📌 How to Run
1. Clone the repository:
   ```bash
   git clone <repo_link>
   cd weather-forecasting
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the main script:
   ```bash
   python src/train_forecast.py
   ```
4. View results in the `results/` folder.

## 🤝 Contributing
Feel free to contribute by opening issues or submitting pull requests.

## 📜 License
This project is open-source under the MIT License.

