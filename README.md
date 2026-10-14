# Measuring Gender Bias in AI-Based Recruitment Using Demographic Parity and Equal Opportunity

## Overview

This project investigates gender fairness in AI-based recruitment using two fairness metrics: **Demographic Parity (DP)** and **Equal Opportunity (EO)**.

AI-based recruitment systems can help automate hiring decisions, but their predictions may produce different outcomes for different demographic groups. This research examines how the choice of fairness metric affects the evaluation of gender bias in a recruitment classification model.

A Logistic Regression classifier is trained to predict hiring decisions. Demographic Parity and Equal Opportunity are then used to evaluate its predictions across gender groups.

## Research Question

**How does the choice between Demographic Parity and Equal Opportunity affect the evaluation of gender fairness in AI-based recruitment decisions?**

## Objectives

- Develop a machine learning model to predict recruitment decisions.
- Evaluate model performance using standard classification metrics.
- Measure gender fairness using Demographic Parity and Equal Opportunity.
- Compare the findings from both fairness metrics.
- Discuss the limitations of evaluating fairness using a single dataset and model.

## Dataset

The study uses the publicly available *AI Fair Recruitment Dataset* from Kaggle.

**Source:** https://www.kaggle.com/datasets/roiiith/ai-fair-recrutment-dataset

The dataset contains recruitment-related information, including candidate scores, experience, education, and gender, alongside the hiring decision.

The original dataset contains 121,200 rows and 16 columns. Data preprocessing includes removing duplicate records and handling missing values.

After preprocessing, the cleaned dataset contains **119,971 rows and 16 columns**.

> Note: The dataset's original licence and generation method should be verified before redistributing the data. The cleaned dataset should not be redistributed unless its licence permits it.

## Methodology

The project follows these main steps:

1. **Data exploration:** Examine the dataset's structure, distributions, missing values, duplicate records, and hiring outcomes.
2. **Data preprocessing:** Remove duplicate records, handle missing values, and prepare features for model training.
3. **Model training:** Train a Logistic Regression classifier using an 80:20 stratified train-test split.
4. **Model evaluation:** Evaluate predictions using accuracy, precision, recall, F1-score, and a confusion matrix.
5. **Fairness analysis:** Calculate Demographic Parity and Equal Opportunity across gender groups.
6. **Comparison:** Examine how the two metrics provide different perspectives on gender fairness.

Preprocessing transformations are fitted on the training data and then applied to the test data to reduce the risk of data leakage.

### Model

The study uses **Logistic Regression** as its classification model.

The target variable is `Hiring_Decision`, where `1` represents a hiring decision and `0` represents a rejection.

### Fairness Metrics

**Demographic Parity (DP)**

Measures whether different gender groups have similar positive prediction rates.

**Equal Opportunity (EO)**

Compares true positive rates across groups among candidates classified as qualified according to the study's qualification definition.

For Equal Opportunity, the study uses a qualification proxy based on candidate assessment scores. Since this proxy is not an independently verified ground-truth qualification label, the resulting fairness measurements must be interpreted with caution.

## Repository Structure

```text
AI-Biasness/
├── data/
│   ├── raw/
│   │   └── recruitment.csv
│   └── processed/
│       └── cleaned_recruitment.csv
├── figure/
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_data_preprocessing.ipynb
│   ├── 03_model_training.ipynb
│   └── 04_fairness_analysis.ipynb
├── paper/
├── result/
│   └── model_predictions.csv
├── src/
└── README.md
```

## Model Performance

The Logistic Regression model achieved the following results on the test set:

| Metric | Score |
|---|---:|
| Accuracy | 98.55% |
| Precision | 97.11% |
| Recall | 97.26% |
| F1-score | 97.19% |

These results describe the model's classification performance. They do not, by themselves, establish that the model is fair across gender groups.

## Results and Interpretation

The fairness analysis compares the predicted hiring rates and true positive rates across gender groups.

Demographic Parity evaluates differences in positive prediction rates, while Equal Opportunity focuses on differences in true positive rates among candidates considered qualified under the study's proxy definition.

The two metrics evaluate different aspects of fairness, so their results should be interpreted in the context of the research question, the dataset, and the qualification proxy.

Refer to the research paper and the fairness analysis notebook for the detailed findings.

## Limitations

- The study uses one dataset and one classification model.
- The dataset's representativeness of real-world recruitment is not established.
- The qualification proxy may not accurately represent actual candidate qualifications.
- Fairness metrics capture specific definitions of fairness and cannot represent every ethical consideration in recruitment.
- High classification performance does not guarantee fair outcomes.

## Tools and Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook
- Git and GitHub

## Research Paper

The research paper is available in the `paper/` directory, subject to the files committed to the repository.

## Authors and Acknowledgements

This project was conducted as a collaborative research study on fairness in AI-based recruitment.

We acknowledge the dataset contributors and the research mentor for their guidance.

## Disclaimer

This project is intended for academic research and educational purposes. Its results should not be used as the sole basis for real-world recruitment decisions.
