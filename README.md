# Netflix-Recommendation-System
Netflix’s recommendation system is a personalized algorithm that predicts what you’re most likely to enjoy, based on your viewing behavior, preferences, and similarities with other users. 

# Features
- Data pipeline: Ingestion → cleaning → splitting → feature stores (users/items/interactions).
- Models: User–item CF (ALS), item-based kNN, content-based (TF‑IDF), hybrid ranker (LightGBM/XGBoost).
- Evaluation: Offline metrics (Precision@K, Recall@K, MAP, NDCG), A/B-ready logging.
- Serving: FastAPI endpoint + CLI for batch recommendations.
- Reproducibility: Deterministic seeds, config-driven runs, experiment tracking.
- Scalability: Sparse matrices, incremental retraining, cached embeddings.

# netflix-recommender/
├─ app/
│  ├─ api.py              # FastAPI app (recommendations, health)
│  └─ service.py          # Model loading, request handling
├─ configs/
│  ├─ als.yaml            # Collaborative filtering config
│  ├─ knn.yaml            # Item-based kNN config
│  └─ hybrid.yaml         # Two-stage ranker config
├─ data/
│  ├─ raw/                # Input datasets (ratings, metadata)
│  └─ processed/          # Cleaned splits + features
├─ models/
│  ├─ checkpoints/        # Saved model artifacts
│  └─ registry.json       # Active model pointer
├─ notebooks/             # EDA, experiments (optional)
├─ scripts/
│  ├─ prepare_data.py     # Clean, split, feature build
│  ├─ train.py            # Train selected model
│  ├─ evaluate.py         # Offline metrics
│  └─ recommend.py        # CLI recommendations
├─ tests/                 # Unit tests
├─ requirements.txt
├─ README.md
└─ LICENSE
# Data
- Ratings: user_id, item_id, rating, timestamp
- Metadata: item_id, title, genres, description, year
- Splits: Chronological train/val/test with user-level stratification.
- Cold-start handling: Content-based fallback for new users/items.
# Collaborative filtering (ALS)
- Input: User–item implicit matrix (watch/like).
- Output: Top‑K recommendations via latent factors.
- Config: configs/als.yaml
seed: 42
model:
  type: als
  factors: 64
  regularization: 0.05
  iterations: 20
  alpha: 40            # for implicit feedback
train:
  min_interactions: 5
  eval_k: [5, 10, 20]

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




