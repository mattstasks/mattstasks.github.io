# Classic Movie Identification for Content Discovery

* **Student Name:** Matthew Andrew Lim
* **Student ID:** 4151759P
* **Module:** ITD224 Assignment

## Project Overview

This project develops a supervised classification pipeline to identify movie characteristics associated with classic films and support exploratory content discovery for a streaming platform.

The analysis combines a global movie dataset with an external list of classic movies to create a binary `classic_flag` target variable. Multiple classification models are evaluated to determine whether available movie characteristics can distinguish classic from non-classic movies.

The final model is used to generate predicted classic probabilities and produce a ranked shortlist of non-labelled movies that exhibit characteristics associated with classic content.

## Business Objective

The business objective is to identify movies with characteristics associated with enduring classic status, helping a streaming platform discover potentially valuable catalogue content that may be overlooked by acquisition strategies focused primarily on short-term commercial performance.

The classic candidate ranking is intended to complement other commercial measures, such as predicted ROI, rather than replace human content acquisition decisions.

## Analytical Objective

Identify the characteristics associated with classic movies and develop a classification model to estimate whether a movie exhibits characteristics associated with classic status.

* **Analysis Type:** Supervised Classification
* **Target Variable:** `classic_flag`

  * `1` = Movie matched to the Classic Movies dataset
  * `0` = Movie not matched to the Classic Movies dataset
* **Business Deliverable:** Ranked shortlist of non-labelled movies based on model-estimated classic probability

## Dataset Sources

* **Global Movies Dataset:** `global_movies.csv`

  * Contains approximately 100,000 movie records and movie characteristics such as genre, release year, runtime, ratings, budget, revenue, popularity, awards and franchise status.

* **Classic Movies Dataset:** `classic_movies.csv`

  * Contains approximately 4,000 movies identified as classics.
  * Used to derive the `classic_flag` target variable.

## Data Preparation

Key data preparation steps included:

* Standardising column names
* Removing duplicate records
* Assessing missing values
* Cleaning and normalising movie titles
* Standardising release dates and years
* Validating numerical fields
* Standardising categorical variables
* One-hot encoding nominal categorical features
* Standardising numerical features
* Creating the binary `classic_flag` target variable

## Dataset Matching

The two datasets did not share a common unique movie identifier.

An initial title-based merge identified approximately 893 matching movie titles.

Additional matching methods using title and release year were explored, but inconsistencies between the datasets significantly reduced the number of matches. Cleaned movie title was therefore retained as the primary matching method for the analysis.

The matched movies were labelled as classics, while unmatched records in the master dataset were treated as non-classics.

This matching limitation is acknowledged as a source of potential label noise in the final analytical dataset.

## Class Imbalance

The resulting dataset was highly imbalanced, with approximately:

* 99.1% non-classic movies
* 0.9% classic movies

A stratified train-test split was used to maintain the class distribution between training and testing datasets.

Model performance was evaluated using:

* Precision
* Recall
* F1-score
* ROC-AUC
* PR-AUC

Accuracy was not prioritised because of the severe class imbalance.


## Models Evaluated

The following supervised classification models were evaluated:

1. Logistic Regression
2. Decision Tree
3. Random Forest

Logistic Regression was selected as the final model based on its comparatively stronger recall and F1-score for the classic class.

However, overall model performance remained limited, indicating that the available structured movie characteristics may not sufficiently capture the factors that determine classic status.

## Business Output

The selected Logistic Regression model generates a predicted classic probability for each movie.

Movies already labelled as classics are excluded, and the remaining movies are ranked according to their predicted probability.

The resulting shortlist can be used as an exploratory content discovery tool to identify movies that may warrant further review by content acquisition teams.

The model is intended to support decision-making rather than automatically determine whether a movie should be considered a classic.

## AI Ethics and Responsible Use

Several ethical considerations were incorporated into the analysis:

* **Fairness:** Severe class imbalance and imperfect dataset matching may introduce bias into predictions.
* **Transparency:** Matching assumptions, modelling limitations and performance metrics are clearly documented.
* **Accountability:** Model rankings should be reviewed by human decision-makers rather than used for automated content acquisition decisions.
* **Responsible Interpretation:** A high predicted probability does not mean that a movie will become or should definitively be considered a classic.

Classic status may also depend on abstract factors such as cultural influence, nostalgia, emotional resonance, historical significance and long-term relevance that cannot be fully captured through structured numerical and categorical data.

## Limitations and Future Improvements

Future improvements could include:

* Using datasets with a common unique identifier such as IMDb ID
* Expanding the labelled classic movie dataset
* Improving entity matching between datasets
* Incorporating critic and audience review information
* Exploring sentiment and review-volume analysis
* Adding cultural and critical recognition variables
* Exploring additional resampling and class-imbalance techniques
* Investigating alternative machine learning models

The results also suggest that classic status may be inherently subjective and difficult to quantify. Future analyses could therefore combine structured movie metadata with qualitative and text-based information to better capture the cultural and emotional characteristics associated with classic films.

## Repository Structure

* `Colab_Notebook_Classic_Predictor_Matthew_Lim.ipynb` — Main Google Colab / Jupyter Notebook containing data preparation, dataset matching, feature engineering, classification modelling, evaluation and candidate ranking.
* `global_movies.csv` — Global movie dataset used for model features.
* `classic_movies.csv` — Classic movie dataset used to create the target variable.

## How to Run

1. Clone or download this repository.
2. Open the `Colab_Notebook_Classic_Predictor_Matthew_Lim.ipynb` file in Google Colab or Jupyter Notebook.
3. Ensure the required datasets are uploaded or available at the file paths specified in the notebook.
4. Run the notebook cells sequentially from data preparation through model evaluation.
5. Review the final ranked classic candidate output generated by the selected classification model.
