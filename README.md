# 🎬 Movie Recommender System (TMDB Dataset)

A content-based movie recommender system using cosine similarity that suggests the top 5 most similar movies based on a selected film. Built with Python, Pandas, and Scikit-Learn on the TMDB 5000 Movie Dataset, and deployed as an interactive web application with Streamlit.


## 🚀 Features
* **Content-Based Filtering:** Recommends movies by analyzing similarities across plot overview, genres, keywords, top 3 cast members, and director.
* **Dynamic Movie Posters:** Fetches real-time movie posters dynamically via the TMDB API.
* **Interactive Web UI:** Searchable dropdown menu and 5-column recommendation display powered by Streamlit.


## 🛠️ Tech Stack
* **Language:** Python
* **Libraries:** NumPy, Pandas, Scikit-Learn (`CountVectorizer`, `cosine_similarity`), Pickle, Requests
* **Web Framework:** Streamlit
* **Dataset:** [TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) (`tmdb_5000_movies.csv` & `tmdb_5000_credits.csv`)


## 🧠 Project Workflow
1. **Data Merging & Cleaning:**
   * Merged `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` on the `title` column.
   * Extracted relevant features: `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast` (top 3 actors), and `crew` (director).
   * Removed spaces in multi-word names and tags (`collapse` function) so full names are treated as single unique tokens.
   * Combined all features into a unified `tags` column.

2. **Vectorization & Cosine Similarity:**
   * Converted text `tags` into 5000-dimensional feature vectors using `CountVectorizer(max_features=5000, stop_words='english')`.
   * Calculated pairwise `cosine_similarity` across all movie vectors to find the 5 closest matches for any given movie.

3. **Streamlit Web Application:**
   * Built `app.py` to load the movie list and similarity matrix, allowing users to pick a movie and view the top 5 recommendations along with their official posters fetched from the TMDB API.


## 📂 Repository Files
* `notebook86c26b4f17.ipynb` — Jupyter Notebook containing data preprocessing, feature engineering, and model building.
* `app.py` — Streamlit web application script.
* `requirements.txt` — Python dependencies required to run the app.
* `README.md` — Project documentation.


## 💻 How to Run Locally
1. Clone this repository:
   ```bash
   git clone [https://github.com/your-username/movie-recommender-system-tmdb-dataset.git](https://github.com/your-username/movie-recommender-system-tmdb-dataset.git)
   cd movie-recommender-system-tmdb-dataset
