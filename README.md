# Probabilistic Machine Learning - Final Project

![GitHub license](https://img.shields.io/github/license/AlexandrosKyr/Probabilistic-Machine-Learning-Diffusion-GaussianProcesses)
![GitHub stars](https://img.shields.io/github/stars/AlexandrosKyr/Probabilistic-Machine-Learning-Diffusion-GaussianProcesses?style=social)
![GitHub forks](https://img.shields.io/github/forks/AlexandrosKyr/Probabilistic-Machine-Learning-Diffusion-GaussianProcesses?style=social)

## Previous Work

This project explores **Denoising Diffusion Probabilistic Models (DDPMs)** and **Gaussian Processes (GPs)** for generative modeling and function fitting. It builds upon the following foundational papers:

- **Denoising Diffusion Probabilistic Models**  
  *Jonathan Ho, Ajay Jain, and Pieter Abbeel, 2020*  
  📄 [Paper Link](https://arxiv.org/abs/2006.11239)  

- **Score-Based Generative Modeling through Stochastic Differential Equations**  
  *Yang Song et al., 2021*  
  📄 [Paper Link](https://arxiv.org/abs/2011.13456)  

- **Improved Denoising Diffusion Probabilistic Models**  
  *Nichol and Dhariwal, 2021*  
  📄 [Paper Link](https://arxiv.org/abs/2102.09672)  

- **Classifier-Free Diffusion Guidance**  
  *Ho and Salimans, 2022*  
  📄 [Paper Link](https://arxiv.org/abs/2207.12598)  

🔗 **Project Repository:** [https://github.com/AlexandrosKyr/Probabilistic-Machine-Learning-Diffusion-GaussianProcesses](https://github.com/AlexandrosKyr/Probabilistic-Machine-Learning-Diffusion-GaussianProcesses)  

---

## Table of Contents
- [Based on Previous Work](#-based-on-previous-work)
- [Quantitative Analysis of Diffusion Models](#-quantitative-analysis-of-diffusion-models)
- [Code & Implementation](#️-code--implementation)
- [Results for Diffusion Models](#-results)
- [Function Fitting with Gaussian Processes](#-function-fitting-with-gaussian-processes)
- [Results for Gaussian Processes](#-results-gaussian-processes)
---

## Quantitative Analysis of Diffusion Models

This study explores **variations and extensions** of Denoising Diffusion Probabilistic Models (DDPMs), focusing on:
- **Parameterizations**: Comparing target parameterizations (`ϵ`, `µ`, `x0`)  
- **Guided Diffusion**: Classifier-guided and classifier-free diffusion  
- **Continuous-Time Models**: Variance-preserving (VP), variance-exploding (VE), and sub-variance-preserving (SubVP) stochastic differential equations (SDEs)  

---

## Code & Implementation
This project builds on **UNET-based diffusion models** and extends them with **guided generation** and **continuous-time formulations**. 

✅ **Modified DDPM implementations** for `ϵ`, `µ`, `x0`  
✅ **Added Classifier-Free and Classifier-Guided Diffusion**  
✅ **Implemented VP-SDE, VE-SDE, and SubVP-SDE**  
✅ **Extended Gaussian Processes for constrained function fitting**  

---

## Results

### **Quantitative Performance Comparison of Diffusion Models**

| **Method**              | **FID ↓**          | **Inception Score ↑** | **Log-Likelihood (bits/dim) ↓** | **Training Time (minutes) ↓** |
|-------------------------|-------------------:|----------------------:|-------------------------------:|----------------------------:|
| **Base DDPM**          | 59.69 ± 0.91       | 2.09 ± 0.04           | -23.7633 ± 0.3650              | 09:59                       |
| **DDPM µ**             | 73.86 ± 0.69       | 2.07 ± 0.02           | -26.1582 ± 0.7096              | 10:26                       |
| **DDPM x0**            | 117.58 ± 0.75      | 2.23 ± 0.05           | -99.6665 ± 8.6140              | 10:02                       |
| **VP SDE**             | 201.54 ± 8.92      | 2.09 ± 0.02           | 4.86                            | 08:27                       |
| **VE SDE**             | 164.53 ± 6.45      | 1.95 ± 0.03           | 4.66                            | 08:25                       |
| **Sub-VP SDE**         | 329.71 ± 11.28     | 1.50 ± 0.01           | 7.11                            | 08:32                       |
| **Classifier Guided**  | 55.26 ± 1.22       | 2.11 ± 0.02           | -24.5517 ± 0.3285              | 09:58                       |
| **Classifier-Free**    | 56.10 ± 0.62       | 2.07 ± 0.03           | -24.3048 ± 0.2923              | 11:58                       |

 **Key Observations**:  
- **Classifier-guided diffusion produces higher-quality samples** with better **FID scores**.  
- **Classifier-free diffusion** maintains diversity but performs slightly worse than classifier-guided.  
- **Continuous-time SDE models (VP/VE/SubVP)** show promise for **more structured generative models**, but computational costs remain high.  

## Function Fitting with Gaussian Processes (GPs)

In addition to diffusion models, this project explores **Gaussian Processes (GPs)** for function fitting with constraints.

### **Tasks Studied**
1. **Standard GP Regression**  
   - Compared Maximum A Posteriori (MAP) estimation and No-U-Turn Sampler (NUTS) for kernel hyperparameter tuning.
   - Evaluated predictive performance and uncertainty quantification.

2. **Gaussian Processes with Integral Constraints**  
   - Derived a **constrained posterior distribution** that satisfies integral constraints.
   - Verified theoretical properties (e.g., normality of the constrained distribution).

### **Results for Gaussian Processes**

| **Method**  | **Kernel Lengthscale** | **Kernel Variance** | **Test Log-Likelihood ↑** |
|------------|----------------------:|-------------------:|--------------------------:|
| **MAP GP** | 0.066                 | 1.641 ± 0.064      | **0.394 ± 3.821**        |
| **NUTS GP** | 0.066                 | 1.842 ± 0.100      | **-2.345 ± 4.907**       |

**Key Findings:**
- **MAP outperformed NUTS** in test log-likelihood but had higher variance.
- **NUTS provided a broader posterior exploration**, useful for uncertainty quantification.
- **Integral constraints reduced uncertainty in GP predictions**, improving interpretability.
