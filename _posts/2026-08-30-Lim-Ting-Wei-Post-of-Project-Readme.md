---
layout: post
author: Ting Wei
title: "Recommendation System - Ting Wei"
categories: ITD224
---


# ITD224-Recommendation-system
ITD224 Recommendation system
---
This file is a copy of Ting Wei's Readme, in post form. 

# Movie Recommendation System

This project implements a **movie recommendation system** using **association rule mining** and **content-based similarity** techniques on the MovieLens dataset (`movies.csv` and `ratings.csv` from Kaggle).

## Features

- **Association Rule Mining (FP-Growth)**  
  Mines frequent co-watch patterns from user ratings to recommend movies often watched together.  
  Example: *Users who watched "Toy Story" also watched "Toy Story 2".*

- **Content-Based Similarity (TF-IDF & Sentence Transformers)**  
  Computes semantic similarity between movies based on metadata such as genres and tags, enabling content-driven recommendations.

- **Interactive Movie Search and Recommendation**  
  Users can input a movie title (partial or full), select the correct movie if multiple matches appear, and receive personalized recommendations with confidence, lift, and support metrics.

## Dataset

- **`movies.csv`**: Contains movie metadata including `movieId`, `title`, and `genres`.  
- **`ratings.csv`**: Contains user ratings with `userId`, `movieId`, `rating`, and `timestamp`.

Both datasets are sourced from [MovieLens on Kaggle](https://www.kaggle.com/datasets/grouplens/movielens-20m-dataset).

## How It Works

1. **Data Preparation**  
   Filters user ratings to keep highly rated movies and groups movies watched by each user into transactions.  
   Filters popular movies to reduce noise and improve performance.

2. **Association Rule Mining**  
   Uses the FP-Growth algorithm (via PySpark MLlib or Python libraries) to find frequent itemsets and generate association rules capturing user co-watch behavior.

3. **Recommendation Generation**  
   Given a movie title, the system finds association rules where the movie is in the antecedent and recommends consequent movies ranked by confidence and lift.

4. **Content Similarity (Optional)**  
   Uses TF-IDF or Sentence Transformer embeddings to compute semantic similarity between movies for content-based recommendations.

## Usage

- Train the model or load pre-trained models.  
- Input a movie title to get personalized recommendations.  
- View recommendations with associated metrics and movie genres.

## Notes

- The system balances scalability and accuracy by filtering popular movies and tuning support/confidence thresholds.  
- Saving intermediate results and models avoids long recomputation times.  
- PySpark is used for large-scale mining; smaller datasets can use Python libraries.


---
