---
title: "Bachelor thesis"
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

Abstract: The bankruptcy of Lehman Brothers and near collapse of AIG in 2008 undermined the confidence in large financial institutions operating on the market. This implied that credit value adjustment (CVA) became an important part of accounting and regula- tory standards. The credit default swaps (CDS) spreads of liquid entities are available from the market and used in the calculations of CVA. However, in order to determine CDS spreads of illiquid entities, a proxy method is required. In this research, several machine learning methodologies are considered and compared to current methodologies for proxying the CDS spread. The CDS data comes from several market makers, con- taining over 2000 CDS entities for the trading days 12 September 2018, 12 September 2019 and 14 September 2020. The predictive accuracy of a proxy methodology is not solely influenced by its design, since it also depends on selecting the right explanatory variables. Therefore, this paper discusses the CDS liquidity proxy, i.e., number of con- tributors to analyse the effect of CDS liquidity on the CDS spreads and performance of the proxy methodologies. The results show that a single hidden layer artificial neural network (ANN) outperforms the cross-section method, the benchmark method in our research, on all the three trading days, whereas a single hidden layer bayesian neural network (BNN) performs poorly. Furthermore, the results show that both, a simple and efficient regression tree and random forest model, tend to overfit the CDS data. According to the local interpretable model-agnostic explanation (LIME) technique, the most important explanatory variables for the ANN and random forest method belong to the feature rating. In particular, the rating classes that represent a relatively small number of quotes of the data set are considered as the most important explanatory variables for the methods. Also, this paper finds evidence that the CDS liquidity proxy composite depth has a weak relationship with the CDS spreads and does not improve the performance of accuracy of the machine learning models in general.
