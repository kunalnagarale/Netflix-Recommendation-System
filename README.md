# Netflix-Recommendation-System
Netflix’s recommendation system is a personalized algorithm that predicts what you’re most likely to enjoy, based on your viewing behavior, preferences, and similarities with other users. 

# This web-app contains 3 main pages:
- [Home Page](#home-page)
- [Recommendation Page](#recommendation-page)
- [Movie Detail Page](#movie-detail-page)
- [Netflix Page](#netflix-page)


# Home Page
Here the user can choose list of their favourite movies and series and their preferred language. For example, I have entered a list with 2 Horror Movies(Insidious and Insidious Chapter 2), an action series(Supergirl) and a drama series(Suits) as my list of choices and English and Hindi as my preferred languages. Clicking on the Get Started button the user will see the list of recommendations.

<img width="1919" height="925" alt="Screenshot-HomePage" src="https://github.com/user-attachments/assets/be733644-88b9-44ea-90a0-32e05464dc2b" />

# Recommendation Page
Here the user will get poster images of all the recommended movies and series sorted based upon their IMDb Scores.
<img width="1917" height="925" alt="Screenshot-RecommendationPage2" src="https://github.com/user-attachments/assets/6e7ac794-2d9d-472e-997d-eebb467465ec" />
Clicking on any poster image, the user will be sent to the Movie Details page for the corresponding title.


# Movie Detail Page
Here are the complete details of the user selected title like Genre, Movie Summary, Languages in which movie is available, IMDb scores, Directors, Writers and Actors and so on. User will also find a link at the end of the page for the NEtflix Page of the corresponding title.
<img width="1237" height="909" alt="Screenshot 2026-01-17 180611" src="https://github.com/user-attachments/assets/8807c5f5-7b2d-49c0-a7dc-900eac95a089" />
<img width="1228" height="939" alt="Screenshot 2026-01-17 180645" src="https://github.com/user-attachments/assets/97ac166d-1b4c-4792-8efc-6fb76a71ad61" />
<img width="1233" height="1004" alt="Screenshot 2026-01-17 180715" src="https://github.com/user-attachments/assets/270647e9-8246-466a-bc7d-f352b8244c9c" />

# Netflix Page
This page is not a part of my web-app but an example what the user will see as the Netflix Page if they choose to click on the Netflix Link for the title. You can login into your Netflix account and enjoy watching your selected movie or series from our recommendations.
<img width="1829" height="705" alt="Screenshot 2026-01-17 181015" src="https://github.com/user-attachments/assets/6f33f806-4e01-432c-b85c-e48b506041d2" />

# How To Use

To be able to use this web app locally in a development environment you will need the following:

1) You will need [Git](https://git-scm.com) installed on your computer.

2) Then From your terminal, you should do the following:

```cmd
# Clone this repository
git clone https://github.com/garg-priya-creator/Netflix-Recommendation-System.git

# Go into the repository
cd netflix-recommendation-system

# Install flask (if you already haven't)
pip install flask

```
3) To run this application you don't need to have any special configuration but make sure you don't change the directory of the project otherwise you can recieve errors while you try to run the app.

4) You can run the Netflix React App using the following command from your terminal:

```
# Run the app
>>set FLASK_APP=app.py
>>flask run
```

# Features
- Data pipeline: Ingestion → cleaning → splitting → feature stores (users/items/interactions).
- Models: User–item CF (ALS), item-based kNN, content-based (TF‑IDF), hybrid ranker (LightGBM/XGBoost).
- Evaluation: Offline metrics (Precision@K, Recall@K, MAP, NDCG), A/B-ready logging.
- Serving: FastAPI endpoint + CLI for batch recommendations.
- Reproducibility: Deterministic seeds, config-driven runs, experiment tracking.
- Scalability: Sparse matrices, incremental retraining, cached embeddings.

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

# Author

👤 **Kunal Nagarale**
- Github: [https://github.com/garg-priya-creator](https://github.com/kunalnagarale)
- Linkedin: www.linkedin.com/in/kunal-nagarale-b880031b6
- Email: kunalnagarale92@gmail.com



