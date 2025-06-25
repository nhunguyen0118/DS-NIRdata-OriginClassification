# Vietnamese Black Pepper Origin Classification using NIR Spectroscopy & Machine Learning

This project aims to classify the geographical origin of ground black pepper samples from Vietnam using Near-Infrared (NIR) spectroscopy data and machine learning models.

## Problem Statement

Black pepper from different provinces can differ in chemical composition and quality.  
Authenticating the origin helps protect product value and regional branding, supports Vietnam's initiatives to export high-quality, traceable black pepper to the EU market.

We use NIR spectroscopy - a non-destructive and rapid technique - to analyze pepper powder and build models that predict its province of origin.

## Dataset (confidential)
Due to confidentiality agreements, the raw data is not publicly shared. For code demonstration, synthetic demo files are included under `/sample_data/`.

The raw dataset is collected from ground black pepper measured via NIR machine with structure as follow:
```
📁 NIR data (ground)/
├── Date folders (e.g. 2022-06-23)/
│ └── Code folders (e.g. 00141_27)/
│ └── CSV files of NIR spectra (e.g. Hadamard1_101209_20220623_170624.csv,...)
📄 Info.xlsx → province mapping
```


Each CSV file contains:
- Wavelengths (900–1700 nm)
- Absorbance values per sample


## Workflow Overview

1. **Preprocessing**:  
   - Clean and prepare dataset
   - Apply SNV (Standard Normal Variate): corrects scatter effects
   - Apply 1st or 2nd derivative (Savitzky-Golay filter): enhance peak features
   - StandardScaler: standardizes feature scale: standardizes feature scale
    
2. **EDA(Exploratory Data Analysis)**

PCA was applied only for visualization, with a purpose to confirm that NIR spectra contain relevant information for classification by origin, but also highlights the need for machine learning models to achieve accurate separation.

3. **Modeling Approach**

### Models Tried:
- Logistic Regression
- Support Vector Machine (SVM)
- Random Forest

### Preprocessing Combinations:
- `SNV + Deriv1`
- `SNV + Deriv2`

### Training:
- 80/20 Train/Test Split
- 5-fold Stratified Cross-Validation
- Hyperparameter tuning with `GridSearchCV`

## ✅ Evaluation Metrics

Each model was evaluated using:

Accuracy, F1 Score, Classification Report, Confusion Matrix

## 🎯 Key Insights

- PCA retains variance but discards class-relevant signals in this case.
- Best results were obtained using **full features** with **SVM with SNV + Deriv1**.
- NIR + ML is a promising approach for **geographical traceability** in Vietnamese agricultural products.

## 💡 Future Work

- Test other preprocessing (MSC, baseline correction)
- Try deep learning models (CNN on spectral data)
- Expand dataset for more provinces and harvest seasons

## 📂 Folder Structure (after processing)
```
Capstone Project/
├── sample_data.csv/ #synthetic file for demonstration only
├── capstoneproject.ipynb
├── images/ # PCA plots, confusion matrix, etc.
└── README.md
```
