Movie Recommendation System

This repository contains the code for building a Movie Recommendation System using metadata from the TMDB (The Movie Database) 5000 movies dataset. The goal of this project is to recommend similar movies based on the content of the movie, using natural language processing techniques.

Dataset

The project uses two CSV files:

	•	tmdb_5000_movies.csv: Contains movie metadata such as budget, genres, keywords, cast, crew, popularity, etc.
	•	tmdb_5000_credits.csv: Contains cast and crew information for the movies.

Project Overview

Steps Performed

	1.	Data Loading:
	•	Loaded both tmdb_5000_movies.csv and tmdb_5000_credits.csv using pandas.
	2.	Data Merging:
	•	Merged the movies and credits data on the title column to combine the information from both datasets.
	3.	Data Preprocessing:
	•	Genre and Keywords Extraction: The genres and keywords columns in the dataset were originally in JSON format. Using Python’s ast module, I parsed these JSON objects and extracted only the names of the genres and keywords.
	•	Cast and Crew Processing:
	•	Extracted the top 3 actors from the cast of each movie.
	•	Extracted only the name of the director from the crew column.
	•	Text Tokenization: The overview column was split into individual words to allow for better similarity comparisons later.
	4.	Data Cleaning:
	•	Removed missing values and unnecessary columns from the dataset.
	•	Collapsed multi-word tokens (like actor names or genres) into single words by removing spaces (e.g., Sam Worthington -> SamWorthington).
	5.	Tags Creation:
	•	Combined key columns (overview, genres, keywords, cast, and crew) into a single tags column. This column represents the essence of each movie and is used to compute similarity.
	6.	Text Vectorization:
	•	The tags were used to represent each movie in vector form, making it easier to compare the similarity between different movies.
	7.	Model Building:
	•	Built a basic content-based recommendation system using cosine similarity between the movie tags.
	8.	Final Dataframe:
	•	The final dataframe (new_df) contains only three columns: movie_id, title, and tags. This will be used as input for the recommendation system.

How It Works

	•	The recommendation system works by comparing the tags of a movie with other movies using cosine similarity. The system suggests movies that have the most similar tags to the given movie.

Getting Started

Prerequisites

	•	Python 3.x
	•	Libraries:
	•	pandas
	•	ast
Future Improvements

	•	Implement TF-IDF or word embeddings for more sophisticated movie similarity calculations.
	•	Add more metadata, such as ratings, reviews, or user preferences, to enhance the recommendation quality.

Dataset Source

	•	TMDB 5000 Movie Dataset: Kaggle
