# 🔮 LSTM-Based Energy Consumption Forecasting using PyTorch

This project presents a complete pipeline to predict appliances energy consumption using an **LSTM-based neural network built with PyTorch**. It includes:

- 🧠 Model training using PyTorch
- 🌐 REST API using FastAPI
- 📈 Streamlit dashboard for real-time prediction
- 🖥️ Jupyter notebooks for EDA, modeling, and forecasting

---

## 📁 Project Files Overview

| File                                             | Description                                                              |
| ------------------------------------------------ | ------------------------------------------------------------------------ |
| `energydata_complete.csv`                        | Dataset containing environmental and sensor readings                     |
| `save_scaler.py`                                 | Script to save the scaler after fitting on training data                 |
| `train_lstm.py`                                  | Script to train the LSTM model and save the weights                      |
| `lstm_model.pth`                                 | Trained LSTM model file                                                  |
| `scaler.save` / `scaler_21_features.save`        | Saved scaler used for input normalization                                |
| `app.py`                                         | FastAPI backend that exposes a prediction API                            |
| `streamlit_app.py`                               | Streamlit dashboard for real-time input and prediction                   |
| `dashboard.py`                                   | Script version of the dashboard for CLI/local runs                       |
| `Appliances_Energy_Consumption_Prediction.ipynb` | Jupyter Notebook with full EDA, feature engineering, and model trials    |
| `forecasting_model.ipynb`                        | Final notebook version for LSTM-based energy forecasting using PyTorch   |

---

## 🧠 LSTM Model Summary

- **Architecture**: 2-layer LSTM
- **Input size**: 21 features
- **Sequence length**: 10 time steps
- **Hidden size**: 64
- **Output**: Next-step forecast of `total_energy_use`

---

## ⚙️ Installation & Setup

### 1. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn torch fastapi uvicorn joblib streamlit
```

---

## 🛠️ Execution Steps

### Step 1: Prepare Scaler

```bash
python save_scaler.py
```

Generates `scaler.save` or `scaler_21_features.save` used for feature normalization.

---

### Step 2: Train the Model

```bash
python train_lstm.py
```

- Trains LSTM using 10 time-step windows
- Saves model as `lstm_model.pth`

---

### Step 3: Start FastAPI Server

```bash
uvicorn app:app --reload
```

- Visit: [http://127.0.0.1:8000](http://127.0.0.1:8000)
- Use the `/predict` endpoint by sending a POST request with a list of 210 values (10 time steps × 21 features):

```json
{
  "values": [/* 210 float values */]
}
```

---

### Step 4: Run Streamlit Dashboard

```bash
streamlit run streamlit_app.py
```

Features:

- Interactive data visualization
- Sequence selection via slider
- Real-time prediction and comparison with actual values
- Charts to show `total_energy_use` and `lighting_energy_use`

---

### Step 5: Run Dashboard as Script (Optional)

```bash
python dashboard.py
```

- A simplified version of the Streamlit dashboard
- Displays prediction logic in a CLI-compatible format

---

## 📈 Features Used

21 total input features including:

- `temp_sensor_1` to `temp_sensor_8`
- `humidity_sensor_1` to `humidity_sensor_8`
- `external_temp`, `external_humidity`, `wind_speed_mps`, `atmospheric_pressure`, `dew_point_temp`

---

## ✅ Author

- **Name**: Tangella Rohith Lakshman Kumar
- **Roll No**: 22PA1A12H3
- **Project**: LSTM-Based Energy Consumption Forecasting
- **Technologies**: Python, PyTorch, Streamlit, FastAPI