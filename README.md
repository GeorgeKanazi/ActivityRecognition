# Human Activity Recognition Using Time Series Sensor Data

This project was completed as part of the B.Sc. in Data Science at Ben-Gurion University. It focuses on recognizing human activities based on time series data from motion sensors. The task was framed as a multi-class classification problem involving 18 distinct activities such as walking, using a phone, climbing stairs, and more.

---

## 📂 Project Structure
```
├── Activity_Recognition.ipynb # Main notebook with model training and evaluation
├── Assignment_instructions.docx # Original assignment description
├── Report.pdf # Final report detailing methodology and results
├── data/
│ ├── train.csv # Training data (not included in public repo)
│ └── test.csv # Test data (not included in public repo)
```
---
## 🧠 Objective

The goal of the project is to classify human activity based on sequences of accelerometer (and optionally gyroscope/magnetometer) readings. These sequences vary in length and orientation (x, y, z axes). The model must predict one of 18 possible activities.

---

## 📊 Dataset Overview

- **Sensors**: Accelerometer, Gyroscope, Magnetometer  
- **Axes**: X, Y, Z  
- **Data Types**: Time series sequences  
- **Users**: 8 participants  
- **Sequence Length**: Variable, padded to 4000  
- **Labels**: 18 activity categories  
- **Files**: Some contain only accelerometer data, others include all three sensor types

> ⚠️ **Note:** The dataset is part of a private competition and is **not included** in this repository. Please add your own data to the `/data/` folder if you wish to reproduce the results.

---

## 🔧 Methods Used

### 🧹 Preprocessing
- Extracted accelerometer data only
- Padded sequences to fixed length
- Added Gaussian noise to improve generalization

### 🛠 Classical Machine Learning
- Logistic Regression
- Random Forest (n=100)
- XGBoost

### 🤖 Deep Learning Models
- Simple 1D-CNN
- GRU (Simple & Improved)
- Self-Supervised Pretraining via:
  - Autoencoder
  - Masked Modeling

---

## ✅ Validation Strategy

- 80/20 train-validation split
- No stratification due to label imbalance
- Validation data was randomly sampled from the training set

---

## 📈 Performance Summary

| Model                | Validation Loss | Test Loss |
|---------------------|-----------------|-----------|
| Simple 1D-CNN       | 1.658           | 3.918     |
| Simple GRU          | 0.924           | 1.823     |
| Self-supervised GRU | 0.068           | 2.277     |
| Improved 1D-CNN     | 0.651           | 2.898     |
| Improved GRU        | 0.838           | 1.622     |

---

## 🔬 Key Insights

- GRU models generalized better than CNNs across users
- Self-supervised learning via autoencoder improved feature representation but did not always improve test performance
- The best-performing model was the improved GRU with a learning rate scheduler and additional training epochs

---

## 👥 Authors

- [George Kanazi](https://github.com/GeorgeKanazi)
- [Ammar Mnaa](https://github.com/AmmarMnaa)

---
