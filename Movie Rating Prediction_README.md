## README for Movie Rating Prediction

**Title**: Movie Rating Prediction using User-Based Collaborative Filtering

###  Objective
To predict how a user will rate a movie they haven’t seen, using **user-user collaborative filtering** based on historical ratings. Evaluates model performance using RMSE.

###  Dataset
- **Source**: MovieLens 100K Dataset
- **URL**: `https://files.grouplens.org/datasets/movielens/ml-100k/u.data`
- **Shape**: 100,000 ratings from 943 users on 1,682 movies
- **Rating Scale**: 1–5 stars
- **No missing values** in core columns.

###  Data Preprocessing
1. Loaded data into a pandas DataFrame with columns: `user_id`, `movie_id`, `rating`, `timestamp`.
2. Created a **user-movie rating matrix** using `pivot_table`.
3. Temporarily filled NaNs with 0 to compute cosine similarity (actual prediction ignores zeros).

###  Modeling
- **Algorithm**: User-Based Collaborative Filtering
- **Similarity Metric**: Cosine Similarity (`sklearn.metrics.pairwise.cosine_similarity`)
- **Prediction Logic**:
  - For target user and movie, find top-k most similar users who rated that movie.
  - Compute a **weighted average** of their ratings, using similarity scores as weights.
  - Default: k=5 (excluding self).

###  Evaluation
- **Train/Test Split**: 80% train (80,000 ratings), 20% test (20,000 ratings)
- **Metric**: Root Mean Squared Error (RMSE)
- **Result**: **RMSE ≈ 1.0414** — meaning predictions are typically ~1 star off, which is reasonable for a simple CF model.

###  Sample Output
- Predicted rating for User 1, Movie 2: **3.2** (Actual: 3.0)
- Top 10 predictions from test set shown with actual vs. predicted ratings.

###  Tools Used
- Python, pandas, numpy
- matplotlib
- scikit-learn: `cosine_similarity`, `train_test_split`, `mean_squared_error`
