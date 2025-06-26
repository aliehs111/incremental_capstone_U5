## Project Notes

incremental_capstone_unit5/
├─ data/
│   ├─ Car_Reviews_Database.csv  
│   └─ bike_rental_reviews.csv  
├─ notebooks/
│   ├─ 01_Data_Collection_and_Preprocessing.ipynb  
│   └─ 02_Sentiment_Analysis.ipynb  
├─ instructions.md  
└─ notes.md  


Bike shape: (50000, 2)




=== BIKE REVIEWS ===
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 50000 entries, 0 to 49999
Data columns (total 2 columns):
 #   Column       Non-Null Count  Dtype 
---  ------       --------------  ----- 
 0   review_text  50000 non-null  object
 1   sentiment    50000 non-null  object
dtypes: object(2)
memory usage: 781.4+ KB

Missing values per column (bike):
review_text    0
sentiment      0
dtype: int64

- ***only 300 unique rows. all others are duplicates***

- after running all the steps then deciding to run them again exactly the same but with only the 300 unique rows, this is the current structure
```
- incremental_capstone_unit5/
├─ data/
│ ├─ bike_rental_reviews.csv
│ ├─ df_bike_clean.pkl
│ ├─ X_reviews.pkl
│ ├─ y_reviews.pkl
│ ├─ df_unique.pkl
│ ├─ X_unique.pkl
│ └─ y_unique.pkl
├─ notebooks/
│ ├─ 01_Data_Collection_and_Preprocessing.ipynb
│ ├─ 02_Sentiment_Analysis.ipynb
│ ├─ 03_Deduplicate_and_Preprocessing.ipynb
│ └─ 04_Sentiment_Analysis_Deduped.ipynb
├─ instructions.md
└─ notes.md
```


---

### Initial Data Load (Bike Reviews)
- **Raw shape:** 50 000 rows × 2 columns (`review_text`, `sentiment`)
- **Missing values:** none
- **Unique reviews:** only ~300 unique `review_text` entries (rest are duplicates)

---

### Task 1: Data Collection & Preprocessing
1. **Loaded** `bike_rental_reviews.csv` into `df`  
2. **Cleaned** text with:
   - lowercasing  
   - removing punctuation  
   - stopword removal  
   - lemmatization  
   Stored in `df['cleaned_review']`.  
3. **Vectorized** cleaned text with TF–IDF → `X_reviews`, labels → `y_reviews`  
4. **Saved** artifacts:
   - `df_bike_clean.pkl`  
   - `X_reviews.pkl`, `y_reviews.pkl`, `vectorizer.pkl`

---

### Task 2: Sentiment Analysis (Original Data)
- **Logistic Regression** → 100 % accuracy / F1  
- **Multinomial Naïve Bayes** → 100 % accuracy / F1  
- **LSTM** → 100 % test accuracy  
- **BERT** → 100 % test accuracy  

*Metrics artificially high due to duplicates across train/test splits.*

---

### Task 3: Deduplication & Preprocessing
1. Dropped duplicate `cleaned_review` rows → `df_unique` (~300 samples)  
2. Re-ran cleaning/vectorization → `X_unique`, `y_unique`  
3. **Saved** deduplicated artifacts:
   - `df_unique.pkl`, `X_unique.pkl`, `y_unique.pkl`, `vectorizer_dup.pkl`

---

### Task 4: Sentiment Analysis (Deduplicated Data)
- **5-fold cross-validation (F1-macro):**  
  - LR: [1.00, 1.00, 1.00, 1.00, 1.00] (mean=1.000)  
  - NB: [1.00, 1.00, 1.00, 1.00, 1.00] (mean=1.000)  
- **Single train/test split** (240 train / 60 test):  
  - LR & NB both 100 % accuracy / F1  

*Even on unique data, sentiment is perfectly separable by keywords.*

---

### Task 5: Key Topic Extraction
- Ran LDA on `cleaned_review` → 10 topics  
- Sample labels & prevalence:
  - Topic 00 **Seat Comfort & Return Process** (8.5 %)  
  - Topic 01 **Prompt Rental Service** (10.0 %)  
  - …  
  - Topic 08 **Wait Times & Process Frustrations** (13.1 %)  
  - Topic 09 **Overall Experience Highlights** (9.9 %)  

---

### Insights & Limitations
- **Dataset simplicity:** Only ~300 unique, templated reviews  
- **Overfitting:** All models hit 100 % → not realistic  
- **Deep models overkill:** LSTM/BERT unnecessary on tiny, clean data  

---

### Next Steps
- **Find a richer corpus** (e.g. Amazon Food Reviews, Yelp, Twitter Airlines)  
- **Re-run pipeline** end-to-end on new data  
- **Compare** model performance on more complex, varied text  
- **Document** differences and updated learnings in a new notes section  

---

## Underwhelming experience
 - As great as “perfect” scores feel, this excercise didn't teach me much because it was essentially plug and play boilerplate following the directions of the assignment. I want to understand this process better so I am going to test it on a better dataset.  Because no matter what I do with the tuning of the models, the accuracy is great but that's not realistic and I'm not learning enough from this excercise.
