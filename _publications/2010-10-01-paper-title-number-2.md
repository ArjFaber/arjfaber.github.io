---
title: "Comparing Machine Learning Methods for Proxying CDS Spreads"
collection: publications
category: manuscripts
permalink: /publication/ml-methods-cds-spreads
excerpt: "An empirical comparison of machine learning techniques for estimating CDS spreads of illiquid entities."
date: 2021-01-01
venue: "University of Groningen – Department of Econometrics, Economics and Finance"
paperurl: "http://arjfaber.github.io/files/BSc_thesis_Arjan_Faber.pdf"
slidesurl: "https://github.com/ArjFaber/Bayesian_Neural_Network/wiki/Post-%5BUpdated-10-November-2024%5D-A-hard-coded-BNN-solution-implemented-for-a-Seattle-weather-dataset"
citation: "Faber, A. (2021). *Comparing Machine Learning Methods for Proxying CDS Spreads*. University of Groningen."
---

# Comparing Machine Learning Methods for Proxying CDS Spreads

## TL;DR

This research compares traditional and machine learning approaches to estimate credit default swap (CDS) spreads for illiquid entities. It finds that **artificial neural networks (ANNs)** outperform benchmark models, while **Bayesian neural networks (BNNs)** and some tree-based methods struggle with overfitting.

📄 [Read the Full Thesis (PDF)](http://arjfaber.github.io/files/BSc_thesis_Arjan_Faber.pdf)  
📊 [Code & BNN Implementation (GitHub)](https://github.com/ArjFaber/Bayesian_Neural_Network/wiki/Post-%5BUpdated-10-November-2024%5D-A-hard-coded-BNN-solution-implemented-for-a-Seattle-weather-dataset)

---

## Background

After the 2008 financial crisis, estimating CDS spreads became critical—especially for **illiquid entities** with no direct market quotes. This study proposes and compares proxy methods for estimating those spreads using both traditional econometric models and machine learning approaches.

## Methods Compared

- **Cross-Section Method** (benchmark)
- **Artificial Neural Network (ANN)**
- **Bayesian Neural Network (BNN)**
- **Regression Trees**
- **Random Forests**

Data includes CDS spreads for over 2,000 entities on selected trading days in 2018, 2019, and 2020.

## Key Findings

- ✅ **ANNs consistently outperform** the benchmark cross-section model.
- ❌ **BNNs underperform**, possibly due to training complexity and over-regularization.
- ⚠️ **Regression trees & random forests** show a tendency to overfit.
- 📉 Liquidity proxies (like number of contributors, composite depth) **do not enhance** model accuracy significantly.
- 🧠 Using **LIME explanations**, credit ratings (especially underrepresented classes) were identified as the most influential features.

---

## 📦 Bayesian Neural Network in TensorFlow

This section provides a walkthrough of a custom BNN model implemented using **TensorFlow** and **TensorFlow Probability**. The goal: to estimate predictive uncertainty in CDS spreads.

### Highlights

- Hard-coded BNN using custom BayesianDenseLayer
- Uses **Flipout sampling** for efficient stochastic gradient estimates
- Includes **KL divergence** loss for regularization
- Predicts both **mean and variance** for regression tasks

📘 See the [BNN Code and tutorial on my GitHub page](https://github.com/ArjFaber/Bayesian_Neural_Network/wiki/Post-%5BUpdated-10-November-2024%5D-A-hard-coded-BNN-solution-implemented-for-a-Seattle-weather-dataset)

---

## 📈 Model Performance

### Example Results (RMSE per Fold)

| Dataset | Fold 1 | Fold 2 | Fold 3 | Mean RMSE |
|--------|--------|--------|--------|-----------|
| Dataset 1 | 0.26696 | 0.27278 | 0.25661 | 0.26545 |
| Dataset 2 | 2.82490 | 0.82044 | 1.20805 | 1.61780 |
| Dataset 3 | 0.27719 | 0.22709 | 0.22254 | **0.24227** |
| Dataset 4 | 0.53035 | 1.20390 | 0.65294 | 0.79573 |

✳️ **Best Performance:** Dataset 3  
❗ **Most Variability:** Dataset 2

---

## 🔮 Key Takeaways

- ANNs are a robust and reliable method for proxying CDS spreads
- BNNs require careful tuning and more data to be competitive
- Some machine learning models overfit without added predictive power
- Interpretable ML (e.g. LIME) helps understand model behavior beyond metrics

---

## 📌 Citation

> Faber, A. (2021). *Comparing Machine Learning Methods for Proxying CDS Spreads*. University of Groningen.

---

## Want to Learn More?

💬 Let me know if you’d like:
- A full walkthrough of the codebase
- An explanation of how variational inference works in BNNs  
- Help deploying this as a blog post or academic page

---

Let me know if you'd like this turned into a **GitHub Pages/Jekyll project template** or need the structure for `index.md`, `_config.yml`, etc. I can help package it up!
