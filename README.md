# 🌦️ Neural Network-based Climate Data Forecasting

This repository presents an in-depth time series forecasting project using advanced deep neural network models to predict temperature trends. Implemented as an 8th semester course project, the goal was to evaluate and compare various deep learning models, including ANN, LSTM, and N-BEATS, and explore ensemble techniques for performance improvement.

---

## 📌 Objective

- Implement and compare neural network-based time series forecasting models.
- Analyze model performance using detailed error metrics.
- Develop ensemble models to improve prediction accuracy.
- Test models on both real-world climate data and synthetic chaotic time series.

---

## 📊 Dataset Description

- **Source**: Temperature data from a region near Pune, India.
- **Frequency**: 3-hour intervals (aggregated to daily averages).
- **Preprocessing**:
  - Missing values handled with **linear interpolation**.
  - Normalized using **Min-Max Scaling** to [0, 1] range.

---

## 🧠 Models Implemented

### 🔹 Artificial Neural Network (ANN)
- Uses previous N days to predict the next day.
- Fully connected layers with ReLU activation.

### 🔹 Long Short-Term Memory (LSTM)
- Captures long-term dependencies in time series.
- Effective for sequential temporal prediction.

### 🔹 N-BEATS (Neural Basis Expansion Analysis for Time Series)
- State-of-the-art deep learning model for time series forecasting.
- Uses stacks, blocks, backcast and forecast mechanisms for long & short-term prediction.

---

## 🤝 Ensemble Techniques

### ✅ Simple Average
- Averages predictions from ANN, LSTM, and N-BEATS models.

### ✅ Weighted Average by Confidence
- Weights inversely proportional to model prediction variance on validation set.

### ✅ Meta Learning Ensemble
- Trains a small ANN on model outputs to learn how to best combine predictions.

---

## 🧪 Error Metrics Used

- **MSE** – Mean Squared Error
- **MAE** – Mean Absolute Error
- **Maximum / Minimum Error**
- **Prediction Variance**
- **Correlation Skill Score**
- **Proportion of Explained Variance**

---

## 📈 Model Evaluation Summary

### 📌 ANN Results

| Lookback | MSE     | MAE     | Corr. Score | Explained Var |
|----------|---------|---------|-------------|----------------|
| 3 days   | 0.00772 | 0.06871 | 0.9056      | 0.7144         |
| 5 days   | 0.00449 | 0.05105 | 0.9062      | 0.6438         |
| 7 days   | 0.00356 | 0.04500 | 0.9057      | 0.7780         |

---

### 📌 LSTM Results

| Lookback | MSE     | MAE     | Corr. Score | Explained Var |
|----------|---------|---------|-------------|----------------|
| 3 days   | 0.00324 | 0.04274 | 0.9042      | 0.8152         |
| 5 days   | 0.00343 | 0.04423 | 0.8993      | 0.8060         |
| 7 days   | 0.00338 | 0.04433 | 0.8996      | 0.8068         |

---

### 📌 N-BEATS Results

| Lookback | MSE     | MAE     | Corr. Score | Explained Var |
|----------|---------|---------|-------------|----------------|
| 3 days   | 0.00290 | 0.03895 | 0.9167      | 0.8322         |
| 5 days   | 0.00294 | 0.03941 | 0.9166      | 0.8310         |
| 7 days   | 0.00295 | 0.03957 | 0.9167      | 0.8314         |

---

## 🧩 Ensemble Model Results

### 🔸 Simple Average
| MSE     | MAE     | Corr. Score | Explained Var |
|---------|---------|-------------|----------------|
| 0.00302 | 0.04146 | 0.9247      | 0.8106         |

---

### 🔸 Meta Model (ANN over model outputs)
| MSE     | MAE     | Corr. Score | Explained Var |
|---------|---------|-------------|----------------|
| 0.00263 | 0.03751 | 0.9226      | 0.8480         |

---

### 🔸 Confidence Weighted Average
| MSE     | MAE     | Corr. Score | Explained Var |
|---------|---------|-------------|----------------|
| 0.02659 | 0.12870 | 0.0123      | -0.3863        |

> 🔴 Observation: Confidence model underperforms significantly.

---

## 🌪️ Chaotic Time Series Evaluation (Lorenz System)

Using Lorenz equation (chaotic system) to assess model robustness.

| Model  | MSE     | MAE     | Corr. Score | Max Error | Min Error |
|--------|---------|---------|-------------|------------|-----------|
| ANN    | 1.17392 | 0.71992 | –           | 4.35       | -4.39     |
| LSTM   | 0.72912 | 0.54816 | –           | 4.61       | -2.56     |
| N-BEATS| 0.44145 | 0.42322 | –           | 3.94       | -1.93     |

> ✅ N-BEATS performs best on chaotic data.

---

## 📊 Visual Analysis

- Distribution of prediction accuracy across different normalized temperature bands.
- Bar plots used to visualize:
  - Model prediction spread
  - Region-wise performance
  - Ensemble comparisons

---

## 🧾 Conclusion

- **N-BEATS** consistently outperformed other models in both real-world and chaotic scenarios.
- **Meta learning ensemble** yielded the best overall performance.
- **Confidence-based ensemble** didn’t generalize well — further tuning needed.
- Neural models are powerful for time series but must be selected based on pattern complexity.

---

## 🚀 Future Work

- Explore more advanced architectures like Transformers or TCN.
- Try attention-based models on climate data.
- Extend evaluation to multivariate time series (humidity, pressure, etc.).
- Integrate explainable AI methods for deeper model insights.

---

## 📚 References

1. Oreshkin et al. (2020) – N-BEATS: Neural Basis Expansion for Interpretable Time Series Forecasting. *ICLR 2020*.
2. Hyndman, R. J. & Athanasopoulos, G. – *Forecasting: Principles and Practice*.
3. SHAP Explainability: https://github.com/slundberg/shap
4. N-BEATS in Keras: https://www.kaggle.com/code/andy8744/beginner-keras-end-to-end-solution-usingnbeats
5. Time Series Forecasting in Python: https://otexts.com/fpp3/
6. Lorenz System Overview: https://en.wikipedia.org/wiki/Lorenz_system

---

## 👤 Author

**Barish Sarkhel**  
Reg. No: 20201242  
8th Semester, IISER Pune  
Course Code: DS 4613  
Supervisor: Dr. Joy Merwin Monteiro

---

## 📎 License

This project is intended for educational and research purposes only.
