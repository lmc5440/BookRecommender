# Book Recommender System

## Data

This project uses two datasets:

- **Goodreads Dataset**: Contains book details such as ISBN, description, genres, author, and title.
- **Amazon Reviews Dataset**: Contains review scores and review texts for books.

The datasets are stored in CSV files inside the `Resources` directory:
- `Resources/goodreads_dataset.csv`
- `Resources/book_reviews.csv`

The code selects only the necessary columns:
- From the Goodreads dataset: `isbn`, `description`, `genres`, `author`, and `title`
- From the Reviews dataset: `Id`, `review/score`, and `review/text`

The datasets are then merged using the Goodreads ISBN and the Amazon review `Id`. After merging, the redundant `Id` column is dropped.

---

## Data Preparation & Processing

After merging the datasets, the following processing steps are performed:

1. **Cleaning List-Like Strings**  
   Some columns (like `genres` and `author`) are stored as strings that look like lists (e.g., `['Fiction', 'Mystery']`). A custom function is used to convert these into proper comma-separated strings.

2. **Combining Text Fields**  
   A new column, `book_info`, is created by concatenating the review text, book description, and genres. This combined text field serves as the basis for further text processing and recommendation.

3. **Text Cleaning**  
   A cleaning function (`clean_func`) is defined to:
   - Convert text to lowercase
   - Remove punctuation and non-letter characters
   - Tokenize the text and remove common English stopwords (using NLTK’s stopwords)

   This function is applied to the `book_info` column so that the text is in a uniform format for analysis.

4. **Sentiment Analysis Setup**  
   The VADER sentiment analyzer from NLTK is initialized and a helper function (`analyze_review`) is created. This function computes the compound sentiment score of a review, which is later used to influence the recommendation process.

---

## Recommendation Logic & Modeling

The core recommendation function (`recommend_book`) operates as follows:

1. **Input Handling**  
   The function accepts two inputs from the user:
   - A book title (for context)
   - A review text

2. **Review Cleaning and Sentiment Analysis**  
   The user’s review is cleaned using the same text cleaning function applied to the dataset. Its sentiment is then analyzed with VADER. Based on the compound sentiment score:
   - If the sentiment is positive (score ≥ 0), the system filters for books with high review scores (≥ 4).
   - Otherwise, it filters for books with lower review scores (< 4).

3. **Vectorization and Similarity Calculation**  
   A TF-IDF vectorizer is used to convert the filtered books’ `book_info` text into numerical vectors. The same vectorizer is used to transform the cleaned user review into a vector. Cosine similarity is then computed between the user review vector and the vectors of the filtered books.

4. **Generating Recommendations**  
   The system identifies the top 5 books with the highest similarity scores. It then creates a list of recommendations showing each book’s title and author. Duplicate titles are avoided in the final recommendations.

---

## User Interface

An interactive web interface is built using Gradio. The interface presents the user with:
- A textbox to enter the book title.
- A textbox to enter their review.

After submitting their input, the interface displays the recommended books based on the processed review and similarity calculations.

Below is an excerpt of the Gradio interface code:

```python
instruction = """
    <h1>Book Recommendations</h1>
    <p>What book did you read recently?</p>
    <p>Enter the title and write a brief review of the book.</p>
    <p>Click 'Submit' to get new book recommendations!</p>
    <br/>
"""

gr_interface = gr.Interface(
    fn=recommend_book,
    inputs=[
        gr.Textbox(label="Title"),
        gr.Textbox(label="Your Review")
    ],
    outputs=gr.Textbox(label="Recommended Books"),
    description=instruction
)
gr_interface.launch(share=True)
