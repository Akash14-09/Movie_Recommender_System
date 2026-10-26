# 🎬 Movie Recommender System

A Content-Based Movie Recommender System that suggests the top 5 most similar movies based on a user's selected film. Built with Python and Scikit-Learn using the TMDB 5000 dataset, and deployed as an interactive web application using Streamlit.


## 🚀 Features
* **Content-Based Filtering:** Recommends movies by analyzing similarities in plot overview, genres, keywords, top 3 cast members, and the director.
* **Dynamic Movie Posters:** Fetches real-time movie posters dynamically via the TMDB (The Movie Database) API.
* **Interactive UI:** Clean, searchable dropdown interface built with Streamlit.


## 🛠️ Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-Learn, NLTK (`PorterStemmer`), Pickle, Requests
* **Frontend / Web Framework:** Streamlit
* **Dataset:** [TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)
* **API:** [TMDB API](https://www.themoviedb.org/documentation/api)



## 🧠 How It Works (Project Workflow)

1. **Data Preprocessing & Merging:**
   * Merged `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` on the movie `title`.
   * Extracted key features: `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast` (top 3 actors), and `crew` (director).
   * Removed spaces between multi-word names/tags (e.g., `Sam Worthington` -> `SamWorthington`) to prevent token confusion.
   * Combined all features into a single `tags` column.

2. **Text Processing & Vectorization:**
   * Applied stemming using NLTK's `PorterStemmer` to reduce words to their root form (e.g., *loving, loved* -> *love*).
   * Converted text tags into 5000-dimensional vectors using the **Bag of Words (BoW)** model (`CountVectorizer` with `max_features=5000` and English stop words removed).

3. **Similarity Calculation:**
   * Computed the **Cosine Similarity** matrix across all 4,806 movie vectors to find the closest matching movies based on angular distance.

4. **Web App & Poster Fetching:**
   * Exported the processed DataFrame (`movie_dict.pkl`) and similarity matrix (`similarity.pkl`) using `pickle`.
   * Built an interactive UI with `Streamlit` (`app.py`) that queries the TMDB API using `movie_id` to display movie titles alongside their official posters.



## 💻 How to Run Locally

### 1. Clone the repository
```bash
git clone [https://github.com/your-username/movie-recommender-system.git](https://github.com/your-username/movie-recommender-system.git)
cd movie-recommender-system
