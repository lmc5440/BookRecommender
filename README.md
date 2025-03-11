# 📚 Book Recommender: A Machine Learning Model  

## 📌 Executive Summary  
This project aims to **recommend book titles** based on a user's inputted book title and/or review text. We utilized **sentiment analysis and cosine similarity** to match books with similar themes and ratings.  

We cleaned, preprocessed, and merged two datasets:  
- **Amazon Books Reviews** *(review ratings & text for over 200 books)*  
- **GoodReads Books Metadata** *(including user ratings, genres, and descriptions)*  

## ⚙️ Installation & Usage  

### **Prerequisites**  
Ensure you have the following installed:  
- **Python 3.x**  
- **pandas**  
- **scikit-learn** *(incl. cosine_similarity)*  
- **numpy**  
- **Gradio**  
- **VADER (via nltk)**  
- **Jupyter Notebook**  
- **Git version control system**  
- **Internet connection for data downloads**  

## 📂 Data Preparation  

### **Datasets Used**  
- **Amazon Books Reviews**  
- **GoodReads Books Metadata**  

These datasets contain **book descriptions, reviews, authors, genres, and ratings**, which help generate meaningful recommendations.  

### **Data Cleaning Process**  
To ensure **high-quality and relevant data**, we performed the following preprocessing steps:  

#### **1. Drop Unnecessary Columns**  
Removed columns that do not contribute directly to book recommendations:  
- `track_id`, `playlist_name`, `playlist_id`, `track_artist`,  
  `track_album_release_date`, `track_album_name`,  
  `playlist_genre`, `playlist_subgenre`  

#### **2. Remove Duplicates**  
- Ensured **unique book entries** by eliminating duplicate records.  

#### **3. Convert List-Based Text to Readable Format**  
- Reformatted **genres** and **author** fields to be properly structured as strings.  

#### **4. Apply Text Cleaning**  
- **Converted text to lowercase** for uniformity.  
- **Removed punctuation** and **stopwords** to reduce noise.  
- **Applied tokenization** to split text into meaningful words for better vectorization.  

#### **5. Merge Books and Reviews Datasets**  
- Combined **metadata and review scores** into a single structured dataset.  

---

## 🏗️ Model Methodology  

### **1. Text Preprocessing**  
To improve model performance, we applied various **text preprocessing techniques**:  
- **Stopword Removal**: Eliminates common words to enhance meaningful keyword extraction.  
- **Tokenization**: Splits text into individual words for better feature extraction.  
- **TF-IDF Vectorization**: Converts text into a numerical format to calculate similarities between books.  

### **2. Sentiment Analysis**  
We integrated **sentiment analysis** to refine recommendations:  
- **VADER Sentiment Intensity Analyzer**: Determines the **positivity or negativity** of user reviews.  
- **Filtering Books Based on Sentiment**:  
  - **Positive Reviews (≥4 stars)** → Suggest books with similarly high ratings.  
  - **Negative Reviews (<4 stars)** → Suggest books that received lower ratings with similar themes.  

### **3. Book Recommendation Algorithm**  
The **core recommendation algorithm** follows these steps:  
1. **Vectorize user input review** using **TF-IDF Vectorization**.  
2. **Compute similarity scores** between books using **Cosine Similarity**.  
3. **Retrieve the Top 5 books** with the highest similarity to the user's input.  
4. **Ensure diverse recommendations** by avoiding duplicate book suggestions.  

---

## ⚠️ Challenges Encountered  

While building the recommendation system, we encountered the following challenges:  

- **False Positives & False Negatives**: Some books were recommended due to misleading sentiment analysis.  
- **Data Imbalance**: More reviews exist for popular books, making niche book recommendations more difficult.  
- **Text Complexity**: Some book descriptions were too short, impacting the accuracy of similarity calculations.  

---

## 📊 Key Findings & Results  

### **1. Feature Importance**  
- **Review text** and **book descriptions** were the most significant factors in determining book recommendations.  
- **Sentiment Analysis** played a crucial role in filtering appropriate book suggestions based on the user's mood.  

### **2. Model Evaluation**  
- The **TF-IDF + Cosine Similarity model** provided **strong recommendations**, successfully suggesting highly relevant books.  
- The model was validated by testing it with **real-world book reviews** and **manually cross-checking** the recommendations.  

---

## 🚀 Future Improvements  

To further enhance the **accuracy and effectiveness** of the recommendation system, we plan to implement:  

- **Collaborative Filtering**: Use **user behavior data** to provide more personalized recommendations.  
- **Improved Sentiment Analysis**: Fine-tune sentiment classification for better review understanding.  
- **User Profiles & Personalization**: Track user preferences over time to refine book suggestions based on reading habits.  

---

## 👥 Contributors  
- **Lauren Christiansen**: Project Lead  
- **Ser Yoon**: Engineer  
- **Thomas Tsai**: Engineer  
- **Laetitia Germe Jones**: Engineer  

---

## 🙏 Acknowledgments  
- **Data Providers**: Kaggle, Amazon, and GoodReads for their datasets.  
- **Academic Advisors**: Provided insights into sentiment analysis and recommendation algorithms.  

---

_This README documents the methodology and process behind building our **book recommendation system** using **sentiment analysis and text similarity techniques**._ 📚✨  
