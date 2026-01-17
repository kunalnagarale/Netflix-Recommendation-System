# Netflix-Recommendation-System
Netflix’s recommendation system is a personalized algorithm that predicts what you’re most likely to enjoy, based on your viewing behavior, preferences, and similarities with other users. 

# This web-app contains 3 main pages:
-Home Page

-Recommendation Page

-Movie Detail Page

-Netflix Page

# Home Page
Here the user can choose list of their favourite movies and series and their preferred language. For example, I have entered a list with 2 Horror Movies(Insidious and Insidious Chapter 2), an action series(Supergirl) and a drama series(Suits) as my list of choices and English and Hindi as my preferred languages. Clicking on the Get Started button the user will see the list of recommendations.

<img width="1919" height="925" alt="Screenshot-HomePage" src="https://github.com/user-attachments/assets/be733644-88b9-44ea-90a0-32e05464dc2b" />

# Features
- Data pipeline: Ingestion → cleaning → splitting → feature stores (users/items/interactions).
- Models: User–item CF (ALS), item-based kNN, content-based (TF‑IDF), hybrid ranker (LightGBM/XGBoost).
- Evaluation: Offline metrics (Precision@K, Recall@K, MAP, NDCG), A/B-ready logging.
- Serving: FastAPI endpoint + CLI for batch recommendations.
- Reproducibility: Deterministic seeds, config-driven runs, experiment tracking.
- Scalability: Sparse matrices, incremental retraining, cached embeddings.

# netflix-recommender/
 app/
    api.py              # FastAPI app (recommendations, health)
    service.py          # Model loading, request handling
 configs/
     als.yaml            # Collaborative filtering config
     knn.yaml            # Item-based kNN config
     hybrid.yaml         # Two-stage ranker config
 data/
     raw/                # Input datasets (ratings, metadata)
     processed/          # Cleaned splits + features
 models/
      checkpoints/        # Saved model artifacts
     registry.json       # Active model pointer
notebooks/             # EDA, experiments (optional)
scripts/
     prepare_data.py     # Clean, split, feature build
     train.py            # Train selected model
     evaluate.py         # Offline metrics
     recommend.py        # CLI recommendations
 tests/                 # Unit tests
 requirements.txt
 README.md
 LICENSE
 
# Data
- Ratings: user_id, item_id, rating, timestamp
- Metadata: item_id, title, genres, description, year
- Splits: Chronological train/val/test with user-level stratification.
- Cold-start handling: Content-based fallback for new users/items.

 # Item-based kNN
- Cosine similarity over interaction vectors; fast, interpretable.
- configs/knn.yaml

# Content-based (TF‑IDF)
- Text features from title/description/genres; handles cold-start.

# Hybrid ranker (two-stage)
- Stage 1: Candidate generation (ALS/kNN/content).
- Stage 2: Learning-to-rank (LightGBM/XGBoost) with features:
- User: activity, recency, genre prefs.
- Item: popularity, freshness, embeddings.
- Pair: similarity scores, co-watch stats.

# Acknowledgments
Inspired by classic CF literature, MovieLens datasets, and practical LTR patterns used in production recommenders.




