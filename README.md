# Duplicate_question_pairs
Quora Question Duplicate Detection
This project focuses on detecting whether two Quora questions are duplicates using classical NLP techniques and machine learning models. The goal is to build a pipeline that processes question pairs, extracts meaningful features, and predicts whether both questions have the same intent.

Dataset

The original Quora Question Pairs dataset contains ~400,000 question pairs.
Due to computational constraints, this project was performed on the top 30,000 rows.

Each sample contains:

question1

question2

is_duplicate (target variable)

Project Workflow
1. Data Selection

Selected the top 30,000 rows from the dataset for experimentation.

2. Exploratory Data Analysis (EDA)

Initial EDA was performed to understand:

Distribution of duplicate vs non-duplicate questions

Question length patterns

Word count statistics

Missing values and text characteristics

This helped in understanding how similar duplicate questions tend to be.

3. Baseline Model (Brute Force Approach)
Bag of Words (BoW)

Applied Bag of Words separately on Question1 and Question2

3000 max features selected for each

Total features from BoW:

3000 (Q1) + 3000 (Q2) = 6000 features

Models Used

Random Forest

XGBoost

Baseline Accuracy

≈ 73% accuracy

4. Feature Engineering

To improve performance, several text similarity features were created.

Basic Text Features

Number of characters in Q1

Number of characters in Q2

Number of words in Q1

Number of words in Q2

Number of common words

Total words (Q1 + Q2)

Word share

Word Share formula:

common_words / total_words

Total Features = 6007
5. Model Training After Feature Engineering

Models trained again:

Random Forest

XGBoost

Results

Accuracy improved to:

Random Forest: 76.8%

6. Advanced Feature Engineering

Further improvements were made using token-based, length-based, and fuzzy matching features.

Token Features

cwc_min

cwc_max

csc_min

csc_max

ctc_min

ctc_max

last_word_eq

first_word_eq

Length Based Features

mean_len

abs_len_diff

longest_substr_ratio

Fuzzy Matching Features

fuzz_ratio

fuzz_partial_ratio

token_sort_ratio

token_set_ratio

These features capture semantic similarity and structural similarity between questions.

7. Final Model Performance

After applying advanced feature engineering:

Model	Accuracy
Random Forest	78.4%
XGBoost	79.26%
8. Error Analysis

A key challenge is false positives:

Cases where questions are not duplicates but predicted as duplicates.

This is critical because it can negatively affect user experience on Q&A platforms.

Although XGBoost had slightly higher accuracy,
Random Forest produced fewer misleading duplicate predictions, making it a safer model choice.

Future Improvements

Train on the full dataset (~400k rows)

Apply better preprocessing (stemming, lemmatization)

Use TF-IDF or Word2Vec embeddings

Try TF-IDF weighted Word2Vec

Perform hyperparameter tuning

Use deep learning models (LSTM / BERT)

Use Dask or Vaex for large-scale training
