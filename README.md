# Proposing a Hybrid Approach to Resolving Limitations of Content Based and Collaborative Filtering Recommendation Systems
This project addresses the limitations of traditional content-based and collaborative filtering recommender systems by proposing a hybrid approach. Specifically, it tackles the cold start problem (CSP)—a common issue in recommendation systems where new users or items lack sufficient interaction history. The hybrid model combines content-based filtering (CBF) and collaborative filtering (CF) techniques, leveraging their strengths to improve recommendation accuracy, diversity, and scalability. Using the MovieLens small dataset, this study evaluates the hybrid model's performance against standalone CBF and CF models using metrics like Mean Average Precision at K (MAP@K).
## Datasets
The project uses the publicly available MovieLens small dataset, which includes:
### Ratings Data: 100,836 user ratings for 9,742 movies by 610 users.
### Movies Data: Metadata such as movie titles and genres.
### Features:
Ratings range from 1 to 5.
Genres for each movie are multi-labeled.
User IDs and movie IDs ensure privacy while maintaining unique identification.
## Preprocessing Steps:
### Data Merging: Combined ratings and movies data using movieId as a key.
### Feature Engineering:
Calculated weighted average ratings to mitigate bias from sparsely rated movies.
Addressed class imbalance by down-sampling popular genres and up-weighting underrepresented ones.
### Exploratory Data Analysis (EDA):
Analyzed genre distributions, rating frequencies, and long-tail effects in the dataset.
## Method
The methodology involves building three recommendation models:
### Content-Based Filtering (CBF):
Two approaches were implemented:
Using TF-IDF Vectorizer for feature extraction.
Using MultilabelBinarizer for one-hot encoding genres.
Cosine similarity was calculated to recommend movies based on metadata.
### Collaborative Filtering (CF):
Built using Singular Value Decomposition (SVD) on a user-item interaction matrix.
Sparse matrices were created to handle data sparsity efficiently.
Hyperparameter tuning was conducted by varying latent factors (
k
k).
### Hybrid Model:
Combined recommendations from both CBF and CF models using a weighted union of their outputs.
Weights were adjusted to balance contributions from both models.
## Evaluation Metrics:
### Precision@K: Measures relevance of top-K recommendations.
### MAP@K: Evaluates ranking quality by considering precision across all users.
### Intra-List Similarity Score: Assesses diversity in recommendations.
## Results
### Content-Based Filtering:
The TF-IDF-based model demonstrated better diversity with lower intra-list similarity scores compared to the MultilabelBinarizer-based model.
Precision@K scores ranged between 0.94–1.00, indicating high relevance but limited diversity.
### Collaborative Filtering:
Optimal performance was achieved with k=5 latent factors, balancing precision and overfitting risks.
MAP@K decreased as latent factors increased beyond k=5, consistent with overfitting trends.
### Hybrid Model:
Outperformed standalone models in terms of MAP@K, increasing from 0.016 (CF) to 0.065 (Hybrid).
Achieved greater diversity with reduced intra-list similarity scores, ensuring fairer recommendations
## Future Work
To further improve the hybrid recommendation system, future directions include:
Incorporating implicit feedback (e.g., clickstream data) to enhance user profiles.
Exploring deep learning-based hybrid approaches such as neural collaborative filtering or hybrid autoencoders.
Addressing scalability issues for larger datasets through distributed computing techniques.
Investigating explainable AI methods to make recommendations more interpretable for end-users.
