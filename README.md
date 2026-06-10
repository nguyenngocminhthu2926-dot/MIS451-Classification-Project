# MIS451-Classification-Project
# 🛒 Predicting Online Shoppers' Purchasing Intention

### Performed By

Tran Ngoc Trung Hieu • Nguyen Ngoc Minh Thu • Nguyen Thi Hoai Thuong

---

## 📖 Overview

This project develops and evaluates machine learning classification models to predict whether an online shopping session will result in a purchase.

Using behavioral data collected from an e-commerce website, the study analyzes customer browsing patterns and compares multiple machine learning algorithms to identify the most effective model for predicting purchasing intention.

The objective is to help online retailers identify high-intent visitors and support data-driven marketing decisions that improve conversion rates.

---

## 🎯 Research Question

**Which machine learning classification model best predicts whether an online shopping session will result in a purchase?**

---

## 📊 Dataset

**Dataset:** Online Shoppers Purchasing Intention Dataset

**Source:** UCI Machine Learning Repository

### Dataset Characteristics

* 12,330 online shopping sessions
* 18 features
* Binary target variable (`Revenue`)
* Real-world e-commerce clickstream data
* Data collected over 10 months (February–December, excluding January and April)

### Target Variable

| Variable | Description                                |
| -------- | ------------------------------------------ |
| Revenue  | Whether the session resulted in a purchase |

Dataset Link:

https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset

---

## 🔍 Exploratory Data Analysis

### Class Imbalance

* Purchase sessions: **15.6%**
* Non-purchase sessions: **84.4%**

The dataset is highly imbalanced, making accuracy a misleading metric. Therefore, **F1-Macro** was selected as the primary evaluation metric because it gives equal importance to both purchase and non-purchase classes.

### Strongest Predictor

**PageValues** showed the strongest relationship with purchase behavior. Visitors who reached high-value pages were significantly more likely to complete a purchase.

### Customer Behavior Insights

Higher purchase intention was associated with:

* More product page visits
* Longer product browsing duration
* Higher PageValues

Lower purchase intention was associated with:

* Higher BounceRates
* Higher ExitRates

### Seasonal Trends

November recorded both the highest traffic volume and the highest conversion rate, suggesting strong seasonal effects from promotional events such as Black Friday and Cyber Monday.

---

## ⚙️ Data Preprocessing

### Data Cleaning

* Removed 125 duplicate records
* No missing values detected

### Train-Test Split

* Training Set: 80%
* Test Set: 20%
* Stratified sampling used to preserve class distribution

### Feature Encoding

**VisitorType**

* One-Hot Encoding

**Month**

* Ordinal Encoding

### Feature Scaling

StandardScaler applied to:

* Logistic Regression
* K-Nearest Neighbors (KNN)
* MLP Neural Network

Random Forest used unscaled features.

### Outlier Handling

Outliers were retained because they represent genuine high-engagement customer sessions and contain valuable predictive information.

---

## 🤖 Machine Learning Models

The following classification models were developed and compared:

### Logistic Regression

* Baseline model
* Class-weight balancing applied

### K-Nearest Neighbors (KNN)

* Distance-based classification
* k = 99

### Random Forest

* 200 decision trees
* Balanced class weighting
* Feature importance analysis

### MLP Neural Network

* Hidden layers: (32,16)
* ReLU activation
* Adam optimizer
* Early stopping enabled

---

## 📈 Model Performance

### Cross-Validation Results (10-Fold)

| Model               |   F1-Macro |
| ------------------- | ---------: |
| Logistic Regression |     0.7765 |
| KNN                 |     0.6045 |
| MLP Neural Network  |     0.7669 |
| Random Forest       | **0.8048** |

### Best Model: Random Forest

Random Forest achieved the highest F1-Macro score and the most stable performance across validation folds, making it the selected model for final evaluation.

---

## 🏆 Final Test Results

| Metric    |  Score |
| --------- | -----: |
| Accuracy  | 90.00% |
| Precision | 68.25% |
| Recall    | 67.54% |
| F1-Score  | 67.89% |

The model successfully identified a large proportion of purchase sessions while maintaining strong overall classification performance on unseen data.

---

## 💡 Key Business Insights

The analysis suggests that purchase intention is strongly related to customer engagement.

### High Purchase Intention Indicators

* High PageValues
* More ProductRelated page visits
* Longer ProductRelated browsing duration

### Low Purchase Intention Indicators

* High BounceRates
* High ExitRates

These behavioral signals can be used to support real-time customer targeting and personalization strategies.

---

## 🚀 Business Recommendations

### 1. Prioritize High-Intent Visitors

Use prediction scores and PageValues to identify visitors most likely to purchase and provide timely interventions.

### 2. Improve Product Pages

Enhance:

* Product descriptions
* Product images
* Customer reviews
* Related-product recommendations

### 3. Reduce Bounce and Exit Rates

Optimize:

* Landing pages
* Website speed
* Navigation flow
* Call-to-action placement

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Jupyter Notebook

---

## 📚 References

Sakar, C., & Kastro, Y. (2018). *Online Shoppers Purchasing Intention Dataset*. UCI Machine Learning Repository.

