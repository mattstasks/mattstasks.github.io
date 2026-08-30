# U.S. Movie ROI Proxy Prediction For Content Decision-Making

* **Student Name:** Tan Yan Ling Michelle
* **Student ID:** 9670294V
* **Module:** ITD224 Assignment
* **Individual Objective:** U.S. Movie ROI Proxy Prediction For Content Decision-Making

## Project Overview

This project develops an end-to-end analytics pipeline to predict a **historical U.S. movie ROI Proxy** to support data-driven content acquisition and decision-making.

The project covers data cleaning, scope filtering, exploratory analysis, feature engineering, model benchmarking, hyperparameter tuning, held-out evaluation, subgroup analysis and business-facing ranking.

The model is intended as a **decision-support tool rather than an automated licensing decision system**. The ROI Proxy is a simplified historical financial measure and does not represent actual licensing profitability.

## Dataset Source

* **Dataset:** [Movies Metadata Cleaned Dataset (1900–2025)](https://www.kaggle.com/datasets/mustafasayed1181/movies-metadata-cleaned-dataset-19002025)
* **Source:** Kaggle
* **Final modelling dataset:** 162,463 movies after applying the defined modelling scope and data preparation process.

## Modelling Approach

Five-fold cross-validation was used to benchmark four candidate regression models:

* XGBoost
* LightGBM
* Random Forest
* Ridge Regression

XGBoost achieved the strongest baseline performance and was subsequently tuned using randomly selected hyperparameter combinations.

The tuned XGBoost model achieved:

* **Best hyperparameter-selection CV R²:** 0.6159
* **Held-out test R²:** 0.6163
* **Held-out test MAE:** 0.3897 on the log-transformed ROI Proxy scale

The cross-validation and held-out test R² values were closely aligned, with a difference of 0.0004.

## Business Application

The model generates an illustrative historical ranking of held-out test films based on predicted ROI Proxy. This demonstrates how model predictions could be used as one screening input for content acquisition and portfolio prioritisation.

The predictions are not validated estimates of future financial performance or licensing profitability. Other commercial factors, including audience demand, licensing costs, marketing investment, market fit and platform-specific commercial terms, should also be considered.

## Responsible AI

Five Responsible AI risks were considered:

* Data selection bias
* Pre-release availability
* Target and measurement bias
* Historical bias
* Automation bias

These risks were addressed through transparent scope criteria, leakage controls, subgroup analysis, explicit ROI Proxy labelling and human-in-the-loop positioning.

These controls reduce, but do not eliminate, the identified risks. Historical data may still contain underlying biases, and differences in subgroup performance may affect generalisation across movie genres.

## Conclusion

The model demonstrates useful predictive signal for exploratory screening within the evaluated historical dataset. It should be used as one input to decision-making rather than as a standalone automated decision rule.

Future improvements should focus on incorporating actual licensing costs, stronger pre-release information and additional commercial factors that are not captured in the current dataset.

> **The model should support the decision, not make the decision.**

## Repository Structure

* `9670294v_TanYanLingMichelle_ITD224_Assignment.ipynb` — Main Google Colab/Jupyter Notebook containing data cleaning, exploration, feature engineering, modelling, evaluation, business recommendations and Responsible AI assessment.
* `README.md` — Project overview, dataset source, modelling approach, results and usage information.

## How to Run

1. Clone or download this repository.
2. Open `9670294v_TanYanLingMichelle_ITD224_Assignment.ipynb` in Google Colab or Jupyter Notebook.
3. Ensure the cleaned dataset is available at the required Google Drive path.
4. Run the notebook cells sequentially to reproduce the data preparation, modelling and evaluation workflow.

## Important Note

The results and ranked predictions are based on historical data and are intended for academic and illustrative purposes. They should not be used as standalone evidence for real-world licensing or investment decisions.
