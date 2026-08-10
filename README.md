# 🎬 Movie Recommender System

A content-based movie recommendation system built with Python, FastAPI, Streamlit, TF-IDF, and cosine similarity. The application allows users to search for movies, view movie details, and discover similar movies through an interactive web interface.

## 🚀 Live Demo

👉 https://movie-recommender-system-by-kunal.streamlit.app/

## 📌 Features

- 🔎 Search for movies
- 🎬 View movie details
- 🖼️ Display movie posters and backdrops
- 🤖 Content-based movie recommendations
- 🧠 TF-IDF based similarity
- 🎭 Genre-based recommendations
- 🌐 TMDB API integration
- ⚡ FastAPI backend
- 🎨 Streamlit frontend
- ☁️ Deployed application

## 🧠 How the Recommendation System Works

The system uses a content-based recommendation approach.

Movie information such as:

- Movie overview
- Genres
- Tagline

is combined into a single `tags` feature.

```text
Movie Data
    ↓
Data Cleaning
    ↓
Genre Processing
    ↓
Create Tags
    ↓
Text Preprocessing
    ↓
TF-IDF Vectorization
    ↓
Cosine Similarity
    ↓
Top Similar Movies

```
TF-IDF

The project uses TfidfVectorizer with:

Maximum features: 50,000
N-gram range: (1, 2)
English stopwords

The resulting TF-IDF matrix is used to calculate similarity between movies.

Cosine Similarity

For a selected movie, its TF-IDF vector is compared with the vectors of other movies. Movies with the highest similarity scores are returned as recommendations.

🏗️ System Architecture
```
                    User
                     │
                     ▼
            ┌─────────────────┐
            │ Streamlit       │
            │ Frontend        │
            └────────┬────────┘
                     │ HTTP Requests
                     ▼
            ┌─────────────────┐
            │ FastAPI         │
            │ Backend         │
            └───────┬─────────┘
                    │
          ┌─────────┴──────────┐
          ▼                    ▼
   Recommendation          TMDB API
       Engine                  │
          │                    │
          ▼                    ▼
     TF-IDF Model         Movie Metadata
          │
          ▼
   Recommended Movies

```
📊 Dataset

The project uses a movie metadata dataset containing more than 45,000 movie records.

Important fields used by the recommendation system include:

title
overview
genres
tagline
vote_average
popularity

The recommendation model primarily uses overview, genres, and tagline to create the tags feature.

🔄 Data Preprocessing

The preprocessing pipeline includes:

Removing duplicate records
Removing movies without titles
Handling missing values
Extracting genre names
Combining text features
Converting text to lowercase
Removing punctuation
Removing English stopwords
Lemmatization
📁 Project Structure
```
Movie-recommender-system/
│
├── gitignore
├── .python-version
├── app.py
├── df.pkl
├── indices.pkl
├── main.py
├── movies_metadata.csv
├── movies_recommendation.ipynb
├──requirements.txt
└── tfidf.pkl
```
🔌 API Endpoints

The FastAPI backend provides endpoints for:
```
GET /health
GET /home
GET /tmdb/search
GET /movie/id/{tmdb_id}
GET /recommend/genre
GET /recommend/tfidf
GET /movie/search
```
💻 Installation
1. Clone the repository
git clone https://github.com/Kunalthakur01/movie-recommender-system.git
cd movie-recommender-system
2. Create a virtual environment
python -m venv .venv
3. Activate the environment

Windows:

.venv\Scripts\activate
4. Install dependencies
pip install -r requirements.txt
5. Configure environment variables

Create a .env file:

TMDB_API_KEY=your_tmdb_api_key

Do not commit your .env file to GitHub.

6. Run the FastAPI backend
uvicorn main:app --reload

The API will be available at:

http://127.0.0.1:8000

FastAPI documentation:

http://127.0.0.1:8000/docs
7. Run the Streamlit frontend
streamlit run app.py

The frontend will be available at:

http://localhost:8501
☁️ Deployment

The application is deployed using two services:

Backend

FastAPI backend is deployed on Render.

```
https://movie-recommender-system-6-ajh8.onrender.com
```
Frontend

Streamlit frontend is deployed on Streamlit Community Cloud.

```
https://movie-recommender-system-by-kunal.streamlit.app/
```
📈 Recommendation Logic

For a selected movie:
```
1. Find movie index
        ↓
2. Retrieve its TF-IDF vector
        ↓
3. Calculate similarity with all movies
        ↓
4. Sort similarity scores
        ↓
5. Select highest scores
        ↓
6. Return recommended movies
```
⚠️ Limitations
The system is primarily content-based.
It does not currently use individual user rating history.
Recommendations depend on the available movie metadata.
The system does not implement collaborative filtering.
Movie information depends partly on the TMDB API.
