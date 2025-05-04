# 5Ema_Trading_Strategy

This project uses a trained **Random Forest Regressor** model to predict the **side of a trade** (bullish or bearish) for BTCUSDT based on technical indicators extracted from **two consecutive 15-minute OHLC candles**.

---

## 📌 Requirements

- Python 3.7+
- numpy
- joblib

Install all dependencies using:

```bash
pip install numpy joblib
```
## Input Requirements
The model requires the following input features for prediction:

### From Two Consecutive 15-Minute Candles:
1. **First Candle (Candle-1)**:
   - Open price (O₁)
   - High price (H₁)
   - Low price (L₁)
   - Close price (C₁)
   
2. **Second Candle (Candle-2)**:
   - Open price (O₂)
   - High price (H₂)
   - Low price (L₂)
   - Close price (C₂)

### Technical Indicators (calculated on the second candle):
3. **Exponential Moving Averages**:
   - EMA 5-period (EMA5)
   - EMA 20-period (EMA20)
   - EMA 50-period (EMA50)
   
4. **Average Directional Index**:
   - ADX (14-period recommended)

## Data Format
The model expects input data in the following format (example):

```python
{
    Input : np.array([O₁, H₁, L₁, C₁, O₂, H₂, L₂, C₂, ema5, ema20, ema50, adx])
}
```

```python
# Sample code to use the trained model
import joblib
import numpy as np

# Load the trained model
model = joblib.load('Sell_Random_Forest_Regression_Model_with_adx.pkl')

# Prepare input data
input_data = [42000.0, 42150.0, 41980.0, 42120.0, 42120.0, 42230.0, 42050.0, 42180.0, 42156.78, 42023.45, 41876.32, 28.3]

# Convert to model input format
features = np.array([input_data]) # Don't forget to add one extra square bracket

# Make prediction
prediction = model.predict(features)
print(f"Trade Signal: {prediction[0]}")
```
