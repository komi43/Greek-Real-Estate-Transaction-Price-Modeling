# Greek Real-Estate Transaction Price Modeling

## About the Project

This project is a hands-on journey into data science and machine learning using real-world Greek real-estate transaction data from the official Greek Real Estate Transactions Valuation Register (Μητρώο Αξιών Μεταβιβάσεων Ακινήτων).

The main goal is to **learn how models work from the ground up**. Rather than treating algorithms as black boxes, the project emphasizes understanding their mathematical foundations, the reasoning behind their design, and the trade-offs involved in applying them to real data.

The dataset was chosen deliberately because real-world administrative data comes with imperfections, inconsistencies, limitations and practical challenges that are often absent from artificially generated or ready-to-use datasets. Working through these issues provides an opportunity to develop experience in data preparation, exploratory analysis, feature engineering, model implementation and evaluation.

The project also aims to document the learning process, including the code, experiments, results and limitations encountered along the way.

## Project Status

**Current stage: Deep Neural Network Modeling**

### Completed

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

### Next Steps

- Study the mathematical foundations of artificial neural networks
- Implement a deep neural network for transaction-price prediction
- Understand the roles of network architecture, activation functions, loss functions, optimization and regularization
- Compare the neural network against the established classical machine learning baselines
- Evaluate model performance, generalization and limitations
- Document the findings and lessons learned

## Modeling Objective

> **Estimate the transaction price of a property conditional on its characteristics and intended transaction period.**

## Classical Machine Learning Results

The initial modeling stage established classical machine learning models as baselines for the upcoming neural network experiments.

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Tuned Random Forest | €30,965 | €52,299 | 0.670 |
| Baseline XGBoost | €32,140 | €51,308 | 0.683 |

These results illustrate that model performance depends on the evaluation metric. The Tuned Random Forest achieved the lowest mean absolute error, while Baseline XGBoost achieved the lowest root mean squared error and highest R² among these two models.

Residual analysis also revealed that both models struggle with some higher-value transactions, highlighting limitations that aggregate evaluation metrics alone cannot fully explain.

The results provide a baseline for future experiments rather than a claim that either model is optimal.

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
│   └── 03_classical_machine_learning.ipynb
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
- Jupyter Notebook
- Parquet
- Git and GitHub

## Project Philosophy

This project prioritizes understanding over blindly applying algorithms. Each modeling stage is an opportunity to explore the underlying mathematics, investigate assumptions, experiment with implementation choices, interpret results and learn from limitations.

The objective is not only to build a model that predicts transaction prices, but also to understand **why it behaves as it does, where it succeeds, where it fails, and how different modeling approaches compare**.

The project will evolve as new concepts are studied and implemented, with each notebook documenting a step in that process.