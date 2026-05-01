

##  Project Overview

This project focuses on predicting the **Remaining Useful Life (RUL)** of turbofan engines using the NASA **C-MAPSS dataset**. The goal is to develop and compare multiple machine learning and deep learning models for **predictive maintenance**, reducing unexpected failures and improving operational safety.

---

##  Dataset

We use the NASA **C-MAPSS (Commercial Modular Aero-Propulsion System Simulation)** dataset, which simulates engine degradation over time.

### Key Features:

* Multiple engine units operating under different conditions
* Time-series sensor readings (temperature, pressure, speed, etc.)
* Run-to-failure trajectories
* Separate training and test datasets

### Dataset Subsets:

* **FD001** – 1 operating condition, 1 fault mode
* **FD002** – Multiple operating conditions
* **FD003** – Multiple fault modes
* **FD004** – Most complex (multiple conditions + faults)

---

##  Objectives

* Predict RUL of turbofan engines using sensor data
* Compare **classical ML models vs deep learning models**
* Analyze trade-offs between:

  * Accuracy
  * Model complexity
  * Interpretability
* Identify the most reliable model for real-world deployment

---

##  Methodology

### Data Preprocessing

* Removed irrelevant features
* Engine-wise data splitting (to avoid data leakage)
* RUL computation:

  * Normalized RUL (0 → 1)
* Feature scaling (Z-score normalization using training data only)

---

###  Models Implemented

####  Classical Machine Learning

* Decision Trees
* Support Vector Machines (SVM)
* Ensemble Methods:

  * Bagged Trees
  * Boosted Trees
* Linear Regression variants
* Neural Networks (MATLAB Regression Learner)
* Custom **Random Forest (TreeBagger)** implementation

---

#### Deep Learning Models

* Simple RNN
* LSTM (best performer)
* 1D CNN
* CNN + LSTM hybrid

---

### Training Setup

* Optimizer: Adam
* Epochs: ~40
* Batch size: 64
* Sliding window approach for sequence models

---

## Evaluation Metrics

* RMSE (Root Mean Squared Error)
* MAE (Mean Absolute Error)
* R² Score
* Confusion Matrix (for classification thresholding)

---

## 🏆 Results Summary

| Model         | Test R² | RMSE                 | Notes                     |
| ------------- | ------- | -------------------- | ------------------------- |
| **LSTM**      | ~0.93   | ~0.058               | Best performance          |
| Simple RNN    | ~0.92   | Slightly higher RMSE |                           |
| 1D CNN        | Lower   | Overfitting observed |                           |
| Random Forest | ~0.91   | ~0.069               | Strong classical baseline |
| Bagged Trees  | ~0.91   | ~0.070               | Stable performance        |

---

## Key Insights

* **LSTM outperforms classical models** due to its ability to capture temporal dependencies
* Ensemble methods perform well on tabular data
* Deep learning models require careful tuning to avoid overfitting
* Proper data splitting (engine-level) is critical


## Tools & Technologies

* MATLAB (Regression Learner + Deep Learning Toolbox)
* Python (optional extensions)
* NumPy, Pandas (for preprocessing)

---

## How to Run

1. Download the C-MAPSS dataset
2. Update dataset path in the code
3. Run preprocessing
4. Train models
5. Evaluate results

---

## Future Work

* Implement Transformer-based models
* Improve generalization across operating conditions
* Deploy model for real-time predictive maintenance
* Integrate explainability (SHAP, feature importance)
---

## Author

**Salma Diaa**
PhD Student – Smart Cities Engineering
Western University, Canada

