---
title: "A comparison of Machine Learning Methodologies for Proxing CDS Spreads"
collection: publications
category: manuscripts
permalink: /publication/2010-10-01-paper-title-number-2
excerpt: 'This paper compares machine learning methods for proxying credit spreads.'
date: 2021-01-01
venue: 'University of Groningen (department of econometrics, economics and finance)'
paperurl: 'http://arjfaber.github.io/files/BSc_thesis_Arjan_Faber.pdf'
slidesurl: 'https://github.com/ArjFaber/Bayesian_Neural_Network/wiki/Post-%5BUpdated-10-November-2024%5D-A-hard-coded-BNN-solution-implemented-for-a-Seattle-weather-dataset'
citation: 'Faber A. (2021)'
---

<video width="120%" autoplay loop muted playsinline>
  <source src="http://arjfaber.github.io/files/anim_frontpage.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>


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
- **K-Nearest Neighbours (K-NN)**
- **Regression Trees**
- **Random Forests**

<video width="120%" autoplay loop muted playsinline>
  <source src="http://arjfaber.github.io/files/tree_horizontal_line_merge-2-2.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

Data includes CDS spreads for over 2,000 entities on selected trading days in 2018, 2019, and 2020.

## Bayesian Neural Network in TensorFlow

This section provides a walkthrough of a custom BNN model implemented using **TensorFlow** and **TensorFlow Probability** on a weather dataset. See also the [BNN Code and tutorial on my GitHub page](https://github.com/ArjFaber/Bayesian_Neural_Network/wiki/Post-%5BUpdated-10-November-2024%5D-A-hard-coded-BNN-solution-implemented-for-a-Seattle-weather-dataset)


---

##  Key Takeaways

- ANNs are a robust and reliable method for proxying CDS spreads
- BNNs require careful tuning and more data to be competitive
- Some machine learning models overfit without added predictive power
- Interpretable ML (e.g. LIME) helps understand model behavior beyond metrics

---

## 📌 Citation

> Faber, A. (2021). *Comparing Machine Learning Methods for Proxying CDS Spreads*. University of Groningen.
