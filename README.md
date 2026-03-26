# dual-mutation-ct-radiogenomics
# Paper Title: Robust Multicenter CT Radiogenomics for Dual EGFR and KRAS Prediction in Lung Cancer with Stability-Aware Modeling and SHAP Interpretation

## Overview
This project is implementation of a comprehensive machine learning pipeline for the non-invasive identification of EGFR and KRAS mutations in Non-Small Cell Lung Cancer (NSCLC) using CT-based radiogenomics. It benchmarks handcrafted radiomic features (HRF) against deep representations (DRF) and feature fusion strategies for three-class mutation prediction (wild-type, KRAS-mutant, EGFR-mutant). The study emphasizes generalization across multiple centers using external testing and includes model interpretability via SHAP values.

## Features
*   **Dual Analysis Modes:** Supports both **Supervised** and **Semi-Supervised** learning approaches. The semi-supervised mode utilizes a pseudo-labeling strategy to leverage unlabeled CT scans.
*   **Model Selection & Ranking:** Includes a dedicated post-processing module (available in a separate script [Link](www.placeholder)) that aggregates results from multiple training rotations. It ranks models based on a composite score (balancing high Cross-Validation mean and low standard deviation) and generates a final report of the best-performing configurations.
*   **Interpretability:** Includes SHAP (SHapley Additive exPlanations) calculations to identify key radiomic phenotypes driving predictions. *Note: in this project, SHAP is calculated specifically for handcrafted data.*
*   **Robust Validation:** Utilizes five-fold cross-validation for model tuning and external testing sets to verify generalizability.

## Pipeline Configuration

### Classifiers
We assessed a library of **21** distinct classifiers. Hyperparameters for each classifier–feature-selection combination were tuned using RandomizedSearchCV with five-fold cross-validation; default settings were retained when tuning did not yield improvement.

**Included Models:**
Linear models (Logistic Regression), K-Nearest Neighbors, Decision Trees, ensemble methods (Random Forest, Extra Trees, Gradient Boosting, HistGradientBoosting, AdaBoost, bagging, XGBoost, LightGBM, Voting Classifier, Stacking Classifier), Multilayer perceptrons, Naive Bayes variants (Gaussian, Bernoulli, Complement), Linear Discriminant Analysis, Nearest Centroid, probabilistic models (Gaussian Process), and dummy baselines.

### Dimensionality Reduction & Feature Selection
The project implements **33** different methods for feature selection and extraction to handle high-dimensional radiomic data. Each method produced 50 selected features or components, a number chosen to balance substantial dimensionality reduction with retention of predictive information. Each method was fit on the training data before being applied to the external test data.

**Included Methods:**
Chi-Square, Mutual Information, Correlation Ranking, ANOVA F-test, Information Gain, Univariate Selection, FDR, Variance Threshold, Elastic Net, Random Forest Importance, Permutation Importance, Sequential Selection, Logistic-Regression-based selection, kernel PCA, kernel PCA Poly, Truncated PCA, Isomap, Locally Linear Embedding, multidimensional scaling with different parameters, Factor Analysis, Sparse PCA, NMF, ICA/FastICA, Independent Component Analysis, LDA extraction, UMAP, t-SNE, Spectral Embedding, Diffusion Maps, Random Projections, Sparse Random Projection, Feature Agglomeration, and Autoencoder Deep.

## Supplemental Materials
While top-ranked models are mentioned in the paper, the complete results for other algorithms are available in eight different supplemental files. These files include results for both supervised and semi-supervised learning approaches for HRF, DFR, fused HRF+DFR, aggregation of HRF+DFR+fused, and SHAP values for the HRF dataset. [Link](www.placeholder) 

⁉️ Support
For questions, contact:
Dr. Mohammad R. Salmanpour: msalman@bccrc.ca
