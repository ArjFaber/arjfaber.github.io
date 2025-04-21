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
## Summary
The paper explores how to estimate credit default swap (CDS) spreads for illiquid entities, a need that became more pressing after the 2008 financial crisis eroded trust in large financial institutions. Since CDS spreads are available only for liquid entities, proxy methods are necessary for others. The study compares several machine learning approaches to traditional methods using CDS data from over 2000 entities on three trading days across 2018, 2019, and 2020.

The research finds that a single hidden layer artificial neural network (ANN) consistently outperforms the cross-section method, which serves as the benchmark. In contrast, the single hidden layer Bayesian neural network (BNN) performs poorly. Regression tree and random forest models show a tendency to overfit the data. According to the LIME (Local Interpretable Model-agnostic Explanations) technique, the most important variables influencing ANN and random forest performance are related to credit ratings, especially those from underrepresented rating classes. The study also examines CDS liquidity proxies, such as the number of contributors and composite depth, but finds that these have a weak relationship with CDS spreads and do not significantly enhance model accuracy. Overall, the paper supports the use of ANNs for more accurate CDS spread proxying, while casting doubt on the effectiveness of certain liquidity measures.


## More on Python implementation of Bayesian Neural Networks (BNN)

The rest of this page documents a hard coded Bayesian Neural Network variation implemented with TensorFlow and TensorFlow Probability. This implementation includes Bayesian layers for capturing uncertainty, which is particularly useful for regression tasks where predictions with uncertainty quantification are required.

---

## Contents
1. [Overview](#overview)
2. [Modules and Imports](#modules-and-imports)
3. [Network Components](#network-components)
   - [Initialization](#initialization)
   - [Bayesian Dense Layer](#bayesian-dense-layer)
   - [Bayesian Dense Network](#bayesian-dense-network)
   - [Regression Model (BNN_Reg)](#regression-model-bnn_reg)
4. [Training Functions](#training-functions)
   - [Process and ELBO Calculation](#process-and-elbo-calculation)
   - [Model Evaluation](#model-evaluation)
---

## Overview

This code defines a Bayesian Neural Network (BNN) with hardcoded layers to enable probabilistic inference on neural network weights and biases. Rather than point estimates for weights, this model learns posterior distributions, making it suitable for cases requiring predictive uncertainty.

---

## Modules and Imports

The implementation requires the following packages:
- **NumPy**: For basic array operations.
- **TensorFlow & TensorFlow Probability**: For defining Bayesian components and performing variational inference.
- **scikit-learn**: For calculating performance metrics like RMSE.
- **silence_tensorflow**: Suppresses TensorFlow warnings for cleaner output.

```python
import numpy as np
import tensorflow as tf
import tensorflow_probability as tfp
from sklearn.metrics import mean_squared_error
from silence_tensorflow import silence_tensorflow
```
### Initialization

The model uses **Xavier initialization** to initialize weights, which helps maintain a balance in the flow of gradients. This initialization is crucial for deep networks to ensure efficient training and prevent vanishing or exploding gradients. The weights are initialized with a truncated normal distribution, and the standard deviation is calculated based on the shape of the layer.

```python
def init(shape):
    return tf.random.truncated_normal(
        shape, 
        mean=0.0,
        stddev=np.sqrt(2/sum(shape)))

```

### Bayesian Dense Layer

The `BayesianDenseLayer` class is a custom dense layer that incorporates **Bayesian inference** for uncertainty estimation. Unlike traditional dense layers where the weights and biases are treated as fixed values, this layer treats them as random variables. It enables the model to learn the distributions of weights and biases, which can then be used to estimate the uncertainty in predictions.

#### Key Features:
- **Flipout Sampling**: The layer uses **Flipout sampling** to efficiently estimate the distributions of the weights and biases during the forward pass. This technique reduces the computational cost compared to full Monte Carlo sampling and is particularly useful for large models.
- **KL Divergence**: The loss function includes the **Kullback-Leibler (KL) divergence** between the learned distributions of the weights and biases and a specified prior distribution. This regularization term helps to prevent overfitting by encouraging the learned distributions to be close to the prior.
  
#### Code:

```python
class BayesianDenseLayer(tf.keras.Model):
    def __init__(self, input_data, output_data, name=None):
        super(BayesianDenseLayer, self).__init__(name=name)
        self.input_data = input_data
        self.output_data = output_data
        
        # Initialize weight and bias distributions
        self.weight_loc = tf.Variable(init([input_data, output_data]), name='weight_loc')
        self.weight_std = tf.Variable(init([input_data, output_data]) - 6.0, name='weight_std')
        self.bias_loc = tf.Variable(init([1, output_data]), name='bias_loc')
        self.bias_std = tf.Variable(init([1, output_data]) - 6.0, name='bias_std')
    
    def call(self, x, sampling=True):
        """Forward pass with Flipout sampling for weight and bias perturbations"""
        
        if sampling:
            # Flipout-estimated weight samples
            s = tfp.random.rademacher(tf.shape(x))
            r = tfp.random.rademacher([x.shape[0], self.output_data])
            w_samples = tf.nn.softplus(self.weight_std) * tf.random.normal([self.input_data, self.output_data])
            w_perturbations = r * tf.matmul(x * s, w_samples)
            w_outputs = tf.matmul(x, self.weight_loc) + w_perturbations
            
            # Flipout-estimated bias samples
            r = tfp.random.rademacher([x.shape[0], self.output_data])
            b_samples = tf.nn.softplus(self.bias_std) * tf.random.normal([self.output_data])
            b_outputs = self.bias_loc + r * b_samples
            
            return w_outputs + b_outputs
        else:
            return x @ self.weight_loc + self.bias_loc

    @property
    def losses(self):
        """Calculates KL divergence for weight and bias distributions"""
        weight = tfd.Normal(self.weight_loc, tf.nn.softplus(self.weight_std))
        bias = tfd.Normal(self.bias_loc, tf.nn.softplus(self.bias_std))
        prior = tfd.Normal(0, 1)
        return (tf.reduce_sum(tfd.kl_divergence(weight, prior)) +
                tf.reduce_sum(tfd.kl_divergence(bias, prior)))
```
### Bayesian Dense Network

The `BayesianDenseNetwork` class is a multi-layer network composed of multiple instances of the `BayesianDenseLayer`. This network architecture enables the propagation of uncertainty through multiple layers, where each layer uses Bayesian methods to model weights and biases as distributions rather than fixed values. The final layer of the network outputs the predicted values along with their associated uncertainties.

#### Key Features:
- **Multiple Layers**: The network consists of multiple layers, each represented by a `BayesianDenseLayer`. These layers are stacked to form a deep network capable of learning complex patterns while accounting for uncertainty.
- **Activation Functions**: Each layer applies the **ReLU activation** function (except for the final layer, which outputs raw values without an activation function).
- **Forward Pass**: The forward pass propagates input through each layer, with each layer outputting a distribution of weights and biases. The uncertainty is propagated throughout the network, producing outputs with associated uncertainty.

#### Code:

```python
class BayesianDenseNetwork(tf.keras.Model):
    def __init__(self, dims, name=None):
        super(BayesianDenseNetwork, self).__init__(name=name)
        
        # Initialize layers and activations
        self.steps = []
        self.acts = []
        for i in range(len(dims) - 1):
            self.steps += [BayesianDenseLayer(dims[i], dims[i+1])]
            self.acts += [tf.nn.relu]
            
        self.acts[-1] = lambda x: x  # No activation for the final layer

    def call(self, x, sampling=True):
        """Forward pass through the layers, applying activations"""
        for i in range(len(self.steps)):
            x = self.steps[i](x, sampling=sampling)  # Apply the BayesianDenseLayer
            x = self.acts[i](x)  # Apply activation function
        return x
```
### Regression Model (BNN_Reg)

The `BNN_Reg` class is a Bayesian regression model built on top of the `BayesianDenseNetwork`. It combines a multi-layer neural network for predicting the mean and a variational distribution for modeling observation errors (standard deviation). This model outputs both the predicted values and their associated uncertainties, making it suitable for regression tasks where uncertainty quantification is important.

#### Key Features:
- **Mean Prediction**: The model uses a `BayesianDenseNetwork` to predict the mean of the output.
- **Uncertainty Modeling**: The model also predicts the standard deviation of the output using a Gamma distribution. This enables the model to estimate the uncertainty in its predictions.
- **Bayesian Approach**: By treating both the weights and biases as random variables, the model is able to provide a probabilistic prediction rather than a deterministic one, capturing the uncertainty in the regression task.

#### Code:

```python
class BNN_Reg(tf.keras.Model):
    def __init__(self, dims, name=None):
        super(BNN_Reg, self).__init__(name=name)
        
        # Initialize components for mean and std deviation predictions
        self.loc_mean = BayesianDenseNetwork(dims)
        
        # Variational distribution variables for observation error
        self.std_alpha = tf.Variable([10.0], name='std_alpha')
        self.std_beta = tf.Variable([10.0], name='std_beta')

    def call(self, x, sampling=True):
        """Predicts means and standard deviations for output"""
        
        # Predict means using the BayesianDenseNetwork
        loc_preds = self.loc_mean(x, sampling=sampling)
    
        # Predict std deviation using the Gamma distribution
        post_dist = tfd.Gamma(self.std_alpha, self.std_beta)
        adjust = lambda x: tf.sqrt(tf.math.reciprocal(x))
        N = x.shape[0]
        
        # If sampling is enabled, sample the std deviation
        if sampling:
            std_preds = adjust(post_dist.sample([N]))
        else:
            std_preds = tf.ones([N, 1]) * adjust(post_dist.mean())
    
        # Return both mean and std predictions
        return tf.concat([loc_preds, std_preds], 1)
    
    def ll(self, x, y, sampling=True):
        """Log-likelihood for the Normal distribution"""
        mean_std = self.call(x, sampling=sampling)
        return tfd.Normal(mean_std[:,0], mean_std[:,1]).log_prob(y[:,0])
    
    def Normal_Sampling(self, x):
        """Generate normal samples for predictions"""
        preds = self.call(x)
        return tfd.Normal(preds[:,0], preds[:,1]).sample()

    def sampling(self, x, n=1):
        """Generate multiple samples from the model's distribution"""
        sampling = np.zeros((x.shape[0], n))
        for k in range(n):
            sampling[:, k] = self.Normal_Sampling(x)
        return sampling
    
    @property
    def loss(self):
        """Total loss including KL divergence for the mean and standard deviation"""
        
        # Loss for mean predictions (KL divergence for weights)
        mean_loss = self.loc_mean.losses
        
        # Loss for the standard deviation (KL divergence for Gamma distribution)
        post_dist = tfd.Gamma(self.std_alpha, self.std_beta)
        prior = tfd.Gamma(10.0, 10.0)
        std_loss = tfd.kl_divergence(post_dist, prior)

        # Return the total loss
        return mean_loss + std_loss
```
### Training Functions

The training process involves optimizing the model's parameters using the Evidence Lower Bound (ELBO) method. The key functions involved in the training process are `process` (which calculates the ELBO) and `perform` (which trains the model and evaluates its performance). These functions work together to optimize both the predictive accuracy and the uncertainty quantification of the model.

#### Process and ELBO Calculation

The `process` function calculates the **Evidence Lower Bound (ELBO)**, which is a combination of the **log-likelihood** (how well the model fits the data) and the **KL divergence** (regularization term that penalizes the deviation from prior distributions). This process ensures that the model both learns to make accurate predictions and accounts for the uncertainty in its parameters.

The ELBO is a crucial component of variational inference and ensures that the model is optimized not only for predictive accuracy but also for uncertainty quantification.

#### Code:

```python
def process(model, optimizer, x_data, y_data, N):  
    # Calculating the lower bound (ELBO method)
    with tf.GradientTape() as gradtape:
        ll = model.ll(x_data, y_data)  # Log-likelihood calculation
        model_loss = model.loss  # Total loss (KL divergence + log-likelihood)
        train_cost = model_loss / N - tf.reduce_mean(ll)  # ELBO calculation
    derivatives = gradtape.gradient(train_cost, model.trainable_variables)
    optimizer.apply_gradients(zip(derivatives, model.trainable_variables))
    return train_cost
```

### Model Evaluation

The `perform` function not only handles the training of the model but also evaluates its performance throughout the training process. The evaluation focuses on the accuracy of the model's predictions on the test set, which is measured using the **Root Mean Squared Error (RMSE)**. The model's weights are updated using the **ELBO (Evidence Lower Bound)** method, and performance is tracked across multiple epochs.

The `perform` function iterates through a specified number of training **epochs** and updates the model based on the training data. After each epoch, the model's predictions are compared to the true values from the test data to compute the **RMSE**, which is used as a performance metric.

#### Code:

```python
def perform(model, optimizer, cycles, train_data, test_data, N):
    train_elbo = np.zeros(cycles)  # Store ELBO for each epoch
    mse_root = []  # Store RMSE for each epoch
    y_pred = []  # Store predictions
    y = []  # Store true values

    for ep in range(cycles):
        # Update weights each batch
        for X_values, y_values in train_data:
            train_elbo[ep] += process(model, optimizer, X_values, y_values, N)

        # Evaluate performance on validation data
        for X_values, y_values in test_data:
            y_pred.append(model(X_values, sampling=False)[:, 0])  # Model predictions
            y.append(y_values)  # True values

        # Calculate RMSE
        mse_root.append(calc_rmse(np.asarray(y_pred), np.asarray(y)))

    return mse_root[-1]  # Return final RMSE after training
```
### A possible test output
### Model Performance Evaluation

The following table presents the performance of the Bayesian Neural Network (BNN) across multiple folds and datasets. The metric used for evaluation is **Root Mean Squared Error (RMSE)**, which measures the difference between predicted and actual values, with lower values indicating better performance. The **Mean Performance** is calculated as the average RMSE across all folds for each dataset.

---

#### Performance Across Folds:

##### Dataset 1:
- **Fold 1**: RMSE = 0.26696
- **Fold 2**: RMSE = 0.27278
- **Fold 3**: RMSE = 0.25661
- **Mean Performance**: 0.26545

##### Dataset 2:
- **Fold 1**: RMSE = 2.82490
- **Fold 2**: RMSE = 0.82044
- **Fold 3**: RMSE = 1.20805
- **Mean Performance**: 1.61780

##### Dataset 3:
- **Fold 1**: RMSE = 0.27719
- **Fold 2**: RMSE = 0.22709
- **Fold 3**: RMSE = 0.22254
- **Mean Performance**: 0.24227

##### Dataset 4:
- **Fold 1**: RMSE = 0.53035
- **Fold 2**: RMSE = 1.20390
- **Fold 3**: RMSE = 0.65294
- **Mean Performance**: 0.79573

##### Dataset 5:
- **Fold 1**: RMSE = 0.52259
- **Fold 2**: RMSE = 0.42142
- **Fold 3**: RMSE = 0.37132
- **Mean Performance**: 0.43844

##### Dataset 6:
- **Fold 1**: RMSE = 1.10827
- **Fold 2**: RMSE = 1.22311
- **Fold 3**: RMSE = 0.57080
- **Mean Performance**: 0.96739

##### Dataset 7:
- **Fold 1**: RMSE = 0.33498
- **Fold 2**: RMSE = 0.21589
- **Fold 3**: RMSE = 0.27219
- **Mean Performance**: 0.27436

##### Dataset 8:
- **Fold 1**: RMSE = 0.49992
- **Fold 2**: RMSE = 0.63358
- **Fold 3**: RMSE = 0.88156
- **Mean Performance**: 0.67169

---

#### Overall Mean Performance:

- **Mean performance (RMSE)** across all datasets:  **0.24227**

---

### Summary:
This output shows the performance of the Bayesian Neural Network model across different datasets and folds. The model consistently performs with varying degrees of accuracy, as seen in the RMSE values. Dataset 3 showed the best mean performance, while dataset 2 exhibited a larger spread in RMSE across folds. The overall mean performance of 0.24227 suggests the model is performing reasonably well, with room for improvement in certain datasets.

