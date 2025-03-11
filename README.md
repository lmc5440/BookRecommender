# Book Recommender

This repository contains the code for a Book Recommendation System developed as part of our final project for the Engineering AI Bootcamp (edX/Columbia). The system leverages advanced machine learning techniques—including natural language processing (NLP), sentiment analysis, and cosine similarity—to recommend books based on user-provided reviews and book information.

## Overview

The project combines two datasets:
- **GoodReads Dataset:** Contains book details such as ISBN, description, genres, author, and title.
- **Amazon Reviews Dataset:** Contains user reviews, scores, and review texts for books.

These datasets are merged to create a rich dataset. We then preprocess the text (including cleaning and vectorizing), perform sentiment analysis using VADER, and compute cosine similarity between reviews to generate book recommendations.

## Project Structure

- **Box 1:** Import the books and reviews datasets.
- **Box 2:** Select relevant columns from each dataset and merge them based on the ISBN (for GoodReads) and Id (for Amazon Reviews).
- **Box 3 & Box 4:** Define functions to clean list-like string values (for genres and authors) and convert them into proper string formats.
- **Box 6-9:**  
  - Combine book information (review text, description, genres) into a new column `book_info`.
  - Clean the combined text using NLP techniques (e.g., lowercasing, removing punctuation, filtering stopwords).
  - Set up VADER for sentiment analysis.
- **Box 11-13:**  
  - Define the `recommend_book` function that:
    - Cleans and analyzes a user's input review.
    - Uses the sentiment score to filter books (e.g., selecting books with review scores above or below a threshold).
    - Vectorizes the text using TF-IDF.
    - Computes cosine similarity between the user’s review and book information.
    - Returns the top recommended books.
- **Gradio Interface:**  
  An interactive interface built using Gradio allows users to enter a book title and review, and then displays the recommended books.