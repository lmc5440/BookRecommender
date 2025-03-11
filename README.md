<p align="center">
  <img src="Resources/book_recommender.png" alt="Heart Disease Feature Prediction" width="100%">
</p>

# Executive Summary

In today's digital age, finding the perfect book can be overwhelming with millions of options available. This project tackles that challenge by developing an intelligent Book Recommender System that personalizes book suggestions based on user preferences, ratings, and reviews. By leveraging machine learning, natural language processing, and data analysis, this system helps users discover books that align with their tastes—whether they’re looking for the next bestseller, a hidden gem, or a niche favorite. This analysis delves into the inner workings of our Jupyter Notebook implementation, breaking down how data is processed, recommendations are generated, and insights are drawn.

# Installation & Usage

## Prerequisites

Ensure you have the following dependencies installed:

- Python 3.x
- pandas
- Sklearn (including cosine\_similarity)
- numpy
- Keras
- Gradio
- VADER via nltk
- Jupyter Notebook
- Git version control system
- Internet connection for dataset downloads

## Setup

1. Clone the repository:
  
   ```bash
   git clone <rhttps://github.com/lmc5440/BookRecommender.git>
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Launch Jupyter Notebook and open `book_recommendation.ipynb`

# Data Preparation

The notebook utilizes two main datasets:

1. **Goodreads Dataset (****`goodreads_dataset.csv`****)** - Contains metadata about books, including title, author, genre, and ratings.
2. **Book Reviews (****`book_reviews.csv`****)** - Includes user reviews and ratings for books.

## Steps for Data Preparation

1. **Download required datasets**: If needed, ensure datasets are placed in the correct directory.
2. **Verify file integrity**: Check for missing values and ensure proper formatting.
3. **Preprocess the data**: Standardize formats, clean missing values, and prepare text data for analysis.

# Notebook Structure & Analysis

## 1. Data Preprocessing

- **Loading Data**: The notebook uses `pandas.read_csv()` to load the datasets.
- **Handling Missing Values**: It identifies and removes missing or null values to ensure data consistency.
- **Text Processing**: The `nltk` library is used for tokenization, stopword removal, and stemming to refine text data.

## 2. Exploratory Data Analysis (EDA)

- **Visualizations**: The notebook employs `matplotlib` and `seaborn` to generate histograms, bar charts, and scatter plots that highlight rating distributions, most-reviewed books, and user engagement trends.
- **Correlation Analysis**: It investigates relationships between ratings and book attributes to identify influential factors in book popularity.

## 3. Recommendation Algorithms

### Content-Based Filtering

- **Feature Extraction**: The notebook utilizes `TfidfVectorizer` from `sklearn.feature_extraction.text` to convert book descriptions into numerical vectors.
- **Cosine Similarity Calculation**: Using `sklearn.metrics.pairwise.cosine_similarity`, it computes similarity scores between books.
- **Recommendation Generation**: Based on similarity rankings, the system suggests books similar to a given input.

### Collaborative Filtering

- **User-Item Matrix Construction**: A pivot table of users and book ratings is created using `pandas.pivot_table()`.
- **Matrix Factorization (SVD)**: The notebook applies Singular Value Decomposition (SVD) from `scipy.sparse.linalg` to reduce dimensionality and infer user preferences.
- **Predictions**: It generates recommendations based on user-item interactions and similarity scores.

### Hybrid Approaches

A **hybrid recommendation system** combines both **content-based filtering** and **collaborative filtering** to improve recommendation accuracy and diversity. Each method has its strengths and limitations, and integrating them helps mitigate weaknesses while leveraging the benefits of both.

##### Why Hybrid Approaches Improve Recommendation Quality?
1. **Overcoming Data Sparsity**: Collaborative filtering struggles with data sparsity, especially when a new user has rated very few books. Content-based filtering can still provide recommendations based on book attributes (genre, description) without requiring many user interactions.
2. **Balancing Personalization and Exploration**: Content-based filtering suggests books similar to those a user has read, limiting diversity. Collaborative filtering introduces variety by recommending books liked by users with similar preferences.
3. **Reducing Cold-Start Problems**: A new book with no ratings wouldn’t be recommended by collaborative filtering. Content-based filtering ensures that new books are still recommended based on their attributes.
4. **Handling Popularity Bias**: Collaborative filtering tends to recommend widely popular books more frequently. A hybrid system can balance recommendations by including niche books similar to a user’s preferences.

#### How Hybrid Models Work?
There are multiple ways to integrate both methods:
- **Weighted Hybrid**: Assigns a weight to predictions from both methods and averages them.
- **Switching Hybrid**: Uses collaborative filtering when enough ratings exist; otherwise, it falls back on content-based filtering.
- **Mixed Hybrid**: Generates recommendations from both models and presents them together.
- **Feature Augmentation**: Uses collaborative filtering to enhance content-based filtering (e.g., using user preferences as extra features in a content-based model).

## 4. Model Evaluation

- **Root Mean Square Error (RMSE)**: The notebook evaluates collaborative filtering predictions by calculating RMSE.
- **Recommendation Relevance**: Content-based filtering is validated by manually reviewing suggested books and their descriptions.
- **Comparison of Methods**: It contrasts the effectiveness of both techniques based on recommendation diversity and accuracy.

## 5. Interactive Features

- **User Input for Personalized Recommendations**: The notebook provides an interactive interface where users can enter a book title to receive recommendations.
- **Dynamic Visualization**: Generates word clouds and genre-based recommendations to enhance user engagement.

# Key Findings

- **Popular books tend to have higher ratings but also more polarized reviews.**
- **Collaborative filtering captures personalized preferences but requires a large dataset to be effective.**
- **Content-based filtering performs well in suggesting books with similar themes but lacks personalization.**
- **Hybrid approaches could improve recommendation quality by combining both methods.**

# Future Enhancements

- **Incorporate Deep Learning**: Experiment with neural networks for improved recommendation accuracy.
- **Sentiment Analysis on Reviews**: Use NLP techniques to assess review sentiment and refine suggestions.
- **Deploy as a Web Application**: Implement the model in a Flask or Django web app for user-friendly access.

# Contributors

- **Name**: Lauren Christiansen
- **Name**: Seryoon Yun
- **Name**: Laetitia Germe Jones
- **Name**: Tom Tsai


# Acknowledgments

- **Data Providers**: Kaggle
- **Academic Advisors**: Professors and mentors who guided the project
- **Goodreads & Amazon**: For providing the datasets used in the project

