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

### **Setup**  
1. **Clone the repository**:  
   ```bash
   git clone https://github.com/lmc5440/BookRecommender.git
   cd BookRecommender
