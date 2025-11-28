# Complement-Naive-Bayes-

## 🔄 Full Code Flow
### 1. 📦 Import Libraries
1. Loads all required packages for data processing, NLP, feature engineering, visualization, and model training.

# 2. 📥 Download NLTK Resources
1. Downloads stopwords, tokenizers, POS taggers, lemmatizers, VADER lexicon, and opinion lexicon.

# 3. 🗂️ Load Dataset
1. Reads metadata and up to 1M review records from compressed JSON files.
2. Merges them using asin (product ID).
3. Removes unused columns, fills missing values, and deduplicates reviews.

# 4. ✨ Clean Text With Negation Handling
1. Applies advanced preprocessing:
2. Expand contractions (can't → can not)
3. Remove URLs and symbols
4. Tokenize and lemmatize words
5. Keep negators (not, no, never)
6. Apply negation scope to next tokens (e.g., neg_good)
   Produces a cleaned review column.

# 5. 🏷️ Generate Weak Sentiment Labels (VADER)
1. Uses VADER compound score to classify each review as positive, neutral, or negative.

# 6. ⚖️ Balance the Dataset
1. Neutral reviews dominate, so the code up-samples positive and negative classes to match the majority class.

# 7. 🧠 Custom Feature Engineering
1. Builds multiple feature extractors:
2. TF-IDF n-grams (1 to 3-grams, 30k features)
3. VADER sentiment score
4. POS tag ratios (nouns, verbs, adjectives, adverbs)
5. Review metadata (length, avg word length, exclamations, uppercase words)
6. Polarity lexicon counts (positive/negative word ratios)

# 8. 🔀 Train–Test Split
1. Splits data into 80% training and 20% testing with stratified sampling.

# 9. ⚡ Combine Features With FeatureUnion
1. All features are merged into one hybrid feature space and normalized.

# 10. 🤖 Build and Tune Complement Naïve Bayes Model
1. Trains a ComplementNB classifier with a pipeline and tunes parameters (alpha, fit_prior) using GridSearchCV.

# 11. 📊 Evaluate Model
1. Outputs:
  - Accuracy score
  - Classification report (precision, recall, F1)
  - Confusion matrix heatmap for visual performance analysis.
