# Greek Real-Estate Transaction Price Modeling

## About the Project

This project is a hands-on journey into data science, machine learning and deep learning using real-world Greek real-estate transaction data from the official Greek Real Estate Transactions Valuation Register (Μητρώο Αξιών Μεταβιβάσεων Ακινήτων).

The main goal is to **learn how models work from the ground up** for a regression problem through the lense of supervised learning. Rather than treating algorithms as black boxes, the project emphasizes understanding their mathematical foundations, the reasoning behind their design, and the trade-offs involved in applying them to real world data.

The dataset was chosen deliberately because real-world administrative data comes with imperfections, inconsistencies, limitations and practical challenges that are often absent from artificially generated or ready-to-use datasets. Working through these issues provides an opportunity to develop experience in data preparation, exploratory analysis, feature engineering, model implementation and evaluation.

An additional long-term learning objective is to explore other types of supervised learning problems, particularly classification, in a future project. 

The project documents the learning process, including the code, experiments, results and limitations encountered along the way.

## Project Status

**Current status: Completed — Classical Machine Learning and Deep Learning**

### Completed Work

- Consolidation of annual real-estate transaction datasets covering 2017–2026
- Data cleaning and validation
- Definition of a residential-property modeling population
- Feature engineering and variable transformation
- Exploratory data analysis
- Univariate and bivariate analysis
- Correlation analysis
- Development of a transaction-price prediction problem
- Identification and exclusion of target leakage
- Implementation and comparison of classical regression and machine learning models
- Hyperparameter optimization for selected models
- Evaluation using MAE, RMSE, MAPE, median absolute percentage error and R²
- Residual analysis to investigate prediction errors and model limitations
- Study and implementation of artificial neural networks using PyTorch
- Experimentation with different neural network architectures, target transformations and regularization strategies (dropout and weight decay for DNNs)
- Experimentation with different optimization algorithms, including Stochastic Gradient Descent (SGD) and Adam for DNNs
- Implementation of early stopping and validation-based model selection
- Evaluation using chronological train, validation and test periods
- Interpretation of results and documentation of methodological limitations

## Modeling Objective

> **Estimate the transaction price of a property conditional on its characteristics and intended transaction period.**

## Classical Machine Learning Results

The classical machine learning stage established regression models as initial prediction baselines.

| **Model** | **MAE** | **RMSE** | **R²** |
|---|---:|---:|---:|
| Tuned Random Forest | €30,965 | €52,299 | 0.670 |
| Baseline XGBoost | €32,140 | €51,308 | 0.683 |

These results illustrate that model performance depends on the evaluation metric. The Tuned Random Forest achieved the lowest mean absolute error, while Baseline XGBoost achieved the lowest root mean squared error and highest R² among these two models.

Residual analysis also revealed that both models struggle with some higher-value transactions (even after masking / clipping part of the right tail skewness), highlighting limitations that aggregate evaluation metrics alone cannot fully explain.

The results provide a classical machine learning baselines rather than a claim that either model is optimal.

## Deep Learning: PyTorch Neural Networks

The final modeling stage focused on implementing and understanding feedforward artificial neural networks using PyTorch.

Two approaches to target representation were investigated:

- **Original transaction price:** The network predicts transaction prices in their original euro scale, using a standardized target during training.
- **Log-transformed transaction price:** The network learns the logarithm of transaction prices, which changes how prediction errors are treated during optimization.

The experiments also investigated network architecture, activation functions, loss functions, optimization, early stopping and regularization. Alternative regularization configurations were evaluated across multiple random seeds, and validation performance was used to guide model selection.

### 2025 Test Results

The final models were evaluated on transactions from 2025, which were kept separate from the training and validation periods.

| **Model** | **MAE** | **RMSE** | **R²** |
|---|---:|---:|---:|
| Original-target DNN | €34,806 | €52,364 | 0.672 |
| Log-target DNN | €34,079 | €52,706 | 0.668 |

The log-target model achieved a slightly lower MAE, while the original-target model achieved a slightly lower RMSE and a marginally higher R².

### 2026 Forward-Looking Evaluation

An additional evaluation was performed on transactions from January to August 2026.

| **Model** | **MAE** | **RMSE** | **R²** |
|---|---:|---:|---:|
| Original-target DNN | €38,004 | €58,486 | 0.608 |
| Log-target DNN | €37,548 | €58,600 | 0.607 |

The 2026 evaluation provides an additional indication of how the models perform on a later period. Both approaches show weaker performance than on the 2025 test set, while the log-target model retains a small advantage in MAE.

Overall, neither target representation dominates across all evaluation metrics. The experiments highlight the importance of evaluating models from multiple perspectives rather than selecting one solely on the basis of a single score.

**Evaluation note:** The classical machine learning and deep learning experiments use different evaluation strategies. The classical models were initially evaluated using a random split, whereas the neural networks use chronological splits. Their reported metrics should therefore not be interpreted as a direct head-to-head comparison.

## Data Source

The data were obtained from the official Greek Real Estate Transactions Valuation Register:

- [Official source — Greek Real Estate Transactions Valuation Register](https://www.gsis.gr/polites-epiheiriseis/akinhta/mitroo-axion-metabibaseon-akiniton)

Annual datasets were manually downloaded and consolidated into a unified dataset covering transactions from 2017 through 2026.

## Repository Structure

```text
greek-real-estate-data-analysis/
│
├── README.md
│
├── data/
│   ├── README.md
│   ├── raw_data.csv
│   ├── cleaned_data.csv
│   ├── cleaned_data.parquet
│   └── modeling_data.parquet
│
├── notebooks/
│   ├── 01_data_preparation.ipynb
│   ├── 02_descriptive_analysis.ipynb
│   ├── 03_classical_machine_learning.ipynb
│   └── 04_deep_neural_networks.ipynb
│
└── src/
```

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- PyTorch
- Jupyter Notebook
- Parquet
- Git and GitHub

## Project Philosophy

This project prioritizes understanding over blindly applying algorithms. Each modeling stage is an opportunity to explore the underlying mathematics, investigate assumptions, experiment with implementation choices, interpret results and learn from limitations.

The objective is not only to build a model that predicts transaction prices, but also to understand **why it behaves as it does, where it succeeds, where it fails, and how different modeling approaches compare**.

In this sense, this journey was not only an applied modeling exercise, but also as a practical learning experience.