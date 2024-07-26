**Customer Sentiment Analysis: Project Done as Part of Hackathon**


This dataset, while not the same dataset used for the hackathon but similar customer review data, contains over 33,000 anonymized reviews of McDonald's stores in the United States, scraped from Google reviews. It provides valuable insights into customer experiences and opinions about various McDonald's locations across the country. The dataset includes information such as store names, categories, addresses, geographic coordinates, review ratings, review texts, and timestamps.

**Data Description**

**Columns:**

1. reviewer_id: Unique identifier for each reviewer (anonymized)

2. store_name: Name of the McDonald's store

3. category: Category or type of the store

4. store_address: Address of the store

5. latitude: Latitude coordinate of the store's location

6. longitude: Longitude coordinate of the store's location

7. rating_count: Number of ratings/reviews for the store

8. review_time: Timestamp of the review

9. review: Textual content of the review

10. rating: Rating provided by the reviewer


**Steps Performed**

1. Import Libraries

2. Import Data

3. Feature Engineering

4. Describing Dummy Data: Used store address, review time, rating, and unique values present in it.

5. EDA: Exploratory Data Analysis (EDA) with Python involves analyzing and summarizing data to gain insights and understand its underlying patterns, relationships, and distributions.

6. Univariate and Bivariate Analysis of Data: Univariate analysis visualizes a single variable at a time. Bivariate analysis involves the simultaneous analysis of two variables, exploring the relationship between them, and identifying the strength of this association.

7. Data Preprocessing

8. Sentiment Analyzer Using SentimentIntensityAnalyzer: Assign a sentiment intensity score to sentences (passed the preprocessed data from step 7 here).

9. Identifying Sentiments: Using scores from the above step, plotting word count (WordCloud), identifying words with the biggest contribution to sentiment, and identifying words in positive, negative, and neutral sentiment.

10. Split Data: For training and testing.

11. Modeling: For the hackathon, I used TFIDFVectorizer (Term Frequency Inverse Document Frequency) and Multinomial Naive Bayes Classifier. TFIDF is a statistical formula to convert text documents into vectors based on the relevancy of the word. Multinomial Naive Bayes is a probabilistic classifier used to calculate the probability distribution of text data, which makes it well-suited for data with features representing discrete frequencies or counts of events in various natural language processing (NLP) tasks.

I only used **TFIDVectorizer**(Term frequency Inverse document frequency (TFIDF) is a statistical formula to convert text documents into vectors based on the relevancy of the word) and **Multinomial Naive Bayes Classifier** (probabilistic classifier to calculate the probability distribution of text data, which makes it well-suited for data with features that represent discrete frequencies or counts of events in various natural language processing (NLP) tasks) as a pipeline 


**nb_pipeline = make_pipeline(TfidfVectorizer(), MultinomialNB())**


**RESULTS ARE AS FOLLOWS:**

Multinomial Naive Bayes Classifier:

              precision    recall  f1-score   support
    negative       0.83      0.75      0.79      1721
     neutral       0.98      0.22      0.37      1244
    positive       0.73      0.96      0.83      3583
    macroavg       0.85      0.65      0.66      6548
    weighted       0.81      0.77      0.73      6548
    accuracy                           0.77      6548

But in this project i have included 2 more pipelines

1. **svc_pipeline = make_pipeline(TfidfVectorizer(), SVC())**

   
Support Vector Classifier:

              precision    recall  f1-score   support
    negative       0.90      0.88      0.89      1721
     neutral       0.91      0.91      0.91      1244
    positive       0.95      0.96      0.95      3583
    macroavg       0.92      0.92      0.92      6548
    weighted       0.93      0.93      0.93      6548
    accuracy                           0.93      6548

3. **pa_pipeline = make_pipeline(TfidfVectorizer(), PassiveAggressiveClassifier())**

   
Passive Aggressive Classifier:

              precision    recall  f1-score   support
    negative       0.89      0.87      0.88      1721
     neutral       0.89      0.91      0.90      1244
    positive       0.95      0.94      0.94      3583
    macroavg       0.91      0.91      0.91      6548
    weighted       0.92      0.92      0.92      6548
    accuracy                           0.92      6548

Out of these 3 , SVC had the best accuracy results (The Best Model is SVC : 0.93)


I will add 2 more pipelines later

1.**bernoulli_nb_pipeline = make_pipeline(TfidfVectorizer(), BernoulliNB())**

2.**logistic_pipeline = make_pipeline(TfidfVectorizer(), LogisticRegression())**
