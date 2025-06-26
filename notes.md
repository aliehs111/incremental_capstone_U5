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