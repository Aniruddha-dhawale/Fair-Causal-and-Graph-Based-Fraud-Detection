# Fair, Causal, and Graph-Based Fraud Detection
This project presents a comprehensive pipeline for building a financial fraud detection model that is not only accurate but also interpretable and fair. Moving beyond traditional classification, this work integrates graph-based feature engineering, causal inference, and algorithmic fairness auditing to create a more robust and responsible machine learning system.

Precision-Recall Curve of the baseline model, achieving a high AUPRC of 0.8761.

# Core Findings
This project is structured around three key analytical pillars:

## 📈 Predictive Modeling with Graph Embeddings
A transaction network graph was constructed from the data, and Node2Vec was used to generate powerful node embeddings for both transaction originators and destinations.

A baseline LightGBM model enriched with these graph features achieved an excellent AUPRC of 0.876.

Key Insight: The analysis also explores a common pitfall where including certain features can lead to perfect but misleading metrics (1.0 AUPRC), highlighting a potential data leakage risk from embeddings that are too closely tied to the target.

## Causal Inference of Fraud Drivers
Using the DoWhy library, a causal analysis was performed to move beyond correlation and identify causal drivers of fraud.

Key Finding: The results robustly demonstrate that a high transaction amount causes an approximate 1.05% increase in the probability of fraud, even after controlling for a wide range of other features. This finding was validated across multiple estimation methods and a refutation test.

##  Algorithmic Fairness and Bias Mitigation
The baseline model was audited for fairness using the AIF360 toolkit. The audit revealed a significant bias against one group (based on transaction value as a proxy), with an Equal Opportunity Difference of -0.6429.

The Reweighing pre-processing technique was applied to mitigate this bias. The intervention successfully improved fairness, bringing the metric closer to zero (0.2857) while demonstrating the classic accuracy-fairness trade-off with a minor drop in AUPRC.

#  Technologies & Libraries Used
Language: Python 3

Core Libraries: pandas, NumPy, scikit-learn

Modeling: LightGBM, XGBoost

Graph Analysis: NetworkX, node2vec

Causal Inference: DoWhy

Fairness: AI Fairness 360 (AIF360)

Environment: Jupyter Notebook (Google Colab)

 # Dataset
This project uses the PaySim dataset, a synthetic dataset generated using aggregated real-world financial transaction data. It is designed to mimic normal and fraudulent transaction behavior.

The dataset can be downloaded from Kaggle: Synthetic Financial Datasets For Fraud Detection

# Setup and Execution
Prerequisites
Python 3.8+

A Kaggle account and an API token (kaggle.json)
