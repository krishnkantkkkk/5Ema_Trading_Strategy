# 5Ema_Trading_Strategy

This project uses a trained **Random Forest Regressor** model to predict the **side of a trade** (bullish or bearish) for BTCUSDT based on technical indicators extracted from **two consecutive 15-minute OHLC candles**.

---

## 📌 Requirements

- Python 3.7+
- pandas
- scikit-learn
- ta
- joblib
- python-binance

Install all dependencies using:

```bash
pip install pandas scikit-learn ta joblib python-binance
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

```json
{
    Input : np.array([O₁, H₁, L₁, C₁, O₂, H₂, L₂, C₂, "ema5", "ema20", "ema50", "adx"])
}
