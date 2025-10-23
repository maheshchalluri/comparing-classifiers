# 🧠 Comparing Classifiers — Practical Application 17.1

This repository contains a Jupyter Notebook that explores and compares several **machine learning classification algorithms** on a banking dataset from [UCI Machine Learning repository](https://archive.ics.uci.edu/dataset/222/bank+marketing).  
The goal is to determine which model performs best when predicting whether a bank customer will subscribe to a long-term deposit product, based on demographic and marketing data.

---

## 📚 Table of Contents
1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Business Objective](#business-objective)
4. [Data Understanding](#data-understanding)
5. [Data Preparation](#data-preparation)
6. [Baseline Models](#baseline-models)
7. [Model Comparison](#model-comparison)
8. [Model Optimization](#model-optimization)
9. [Key Findings](#key-findings)
10. [Recommendations](#recommendations)


---

## 🧩 Project Overview

This notebook demonstrates the end-to-end process of evaluating multiple **classification algorithms** within a CRISP-DM framework.  
The workflow includes:
- Data understanding and preparation  
- Model training and evaluation  
- Hyperparameter tuning  
- Practical interpretation of results for business use

The project highlights how machine learning can improve marketing outcomes by identifying key patterns in customer behavior.

---

## 📁 Repository Structure

---

### 🧠 Summary
- The notebook contains the full end-to-end analysis and model comparison.  
- The `data/` folder holds both the dataset and the metadata file describing its features.  
- The structure ensures easy replication — open the notebook, load the dataset, and run all cells to reproduce results.

```
.
├── comparing classifier-practical app III.ipynb
├── data/
│   ├── bank-additional.csv
│   ├── bank-additional-full.csv
│   └── bank-additional-names.txt
├── README.md
└── requirements.txt
```
---

## 🎯 Business Objective

A Portuguese bank conducted multiple marketing campaigns to encourage clients to subscribe to long-term deposits.  
Despite broad outreach, success rates remained low.  

This project seeks to answer:
- Which factors influence whether a customer says “yes”?  
- How do different classifiers perform in predicting customer responses?  
- Which model offers the best trade-off between accuracy, interpretability, and efficiency?

By identifying key predictive drivers, the bank can improve campaign targeting and conversion efficiency.

---

## 🧮 Data Understanding

The dataset includes demographic details, loan information, and campaign contact history.  
It’s moderately clean but **imbalanced** — most customers declined the offer.

**Key Observations:**
- Customers with **housing loans** or **university degrees** showed slightly higher conversion rates.  
- **Cellular contact methods** led to better engagement than telephone calls.  
- Campaign-level factors (like contact frequency) often outweighed demographics in predictive strength.

---

## ⚙️ Data Preparation

Steps taken to prepare data for modeling:

- Encoded categorical features using `ColumnTransformer` with one-hot encoding.  
- Applied `LabelEncoder` to the target variable.  
- Split dataset into **70% training** and **30% testing** sets.  
- Addressed imbalance by focusing on precision, recall, and F1-score instead of accuracy alone.  

---

## 🧩 Baseline Model

The Baseline model used : **Logistic Regression**

**Evaluation Metrics**
--------------------------
```
Accuracy : 0.8876
Precision: 0.4438
Recall   : 0.5000
F1-Score : 0.4702
```
**Summary:**  
Accuracy was high (>88%) but recall was low, showing that both models struggled with minority class predictions.

---

## 🧠 Model Comparison

Expanded evaluation included:
- **Logistic Regression**  
- **K-Nearest Neighbors (KNN)**  
- **Decision Tree**  
- **Support Vector Machine (SVM)**  

MODEL COMPARISON RESULTS:
==========================
```
                 Model  Train Time  Train Accuracy  Test Accuracy
0  Logistic Regression      0.2218          0.8872         0.8876
1        Decision Tree      0.9535          0.9256         0.8579
2                  KNN      0.1188          0.8914         0.8739
3                  SVM     63.1119          0.8872         0.8876
```
**Result:**  
Logistic Regression offered the best mix of speed, interpretability, and performance.  
Tree-based and kernel models performed comparably but were more computationally expensive.

---

## 🔧 Model Optimization

**GridSearchCV** was used to fine-tune hyperparameters.
```
                 Model  CV Score  Test Accuracy  \
0  Logistic Regression  0.887239       0.887594   
1        Decision Tree  0.887309       0.887513   
2                  KNN  0.885679       0.887999   

                                         Best Params  Tuning Time  
0  {'model__C': 0.001, 'model__max_iter': 2000, '...    33.532445  
1  {'model__criterion': 'entropy', 'model__max_de...     7.253375  
2  {'model__n_neighbors': 17, 'model__weights': '...   502.758325  
```
All models achieved similar accuracy, but Logistic Regression remained the most practical choice for real-world deployment.

---

## 💡 Key Findings

- **Data imbalance** significantly affected recall and precision scores.  
- **Education level**, **loan status**, and **contact type** were meaningful predictors.  
- **Logistic Regression** provided the best performance-to-complexity ratio.  
- Campaign outcomes were more influenced by **contact strategy** than by static demographics.  

---

## 🚀 Recommendations

1. **Target Strategy:** Focus marketing on clients with housing loans or higher education levels.  
2. **Channel Optimization:** Prioritize cellular contact and modern communication platforms.  
3. **Model Improvement:** Use resampling methods like **class weighting** to improve minority predictions.  
4. **Ongoing Monitoring:** Re-evaluate model accuracy as new campaigns generate data.  

---


