**Customer_Sentiment_Analysis** : Project done as part of hackathon.

This dataset(which is not the dataset the used for hackathon, but a similar customer review data) contains over 33,000 anonymized reviews of McDonald's stores in the United States, scraped from Google reviews. It provides valuable insights into customer experiences and opinions about various McDonald's locations across the country. The dataset includes information such as store names, categories, addresses, geographic coordinates, review ratings, review texts, and timestamps.

**DATA DESCRIPTION:**


Columns :

reviewer_id: Unique identifier for each reviewer (anonymized)

store_name: Name of the McDonald's store

category: Category or type of the store

store_address: Address of the store

latitude: Latitude coordinate of the store's location

longitude: Longitude coordinate of the store's location

rating_count: Number of ratings/reviews for the store

review_time: Timestamp of the review

review: Textual content of the review

rating: Rating provided by the reviewer


**STEPS PERFORMED**
1. Import Libraries
2. Import Data
3. Feature Enginering
4. Describing dummy data being used using store Address ,review Time, rating and unique values present in it.
5. EDA : Exploratory Data Analysis (EDA) with Python involves analyzing and summarizing data to gain insights and understand its underlying patterns, relationships, and distributions.
6. Univariate and Bivariate Analysis of Data : Univariate Analysis is a type of data visualization where we visualize only a single variable at a time. Bivariate analysis is the simultaneous analysis of two variables. It explores the concept of the relationship between two variable whether there exists an association and the strength of this association.
7. Data Preprocessing
8. Sentiment Analyzer using SentimentIntensityAnalyzer : Give a sentiment intensity score to sentences(passed the preprocessed data from step 7 here).
9. Identifying sentiments using scores from above steps , plotting Word count (WordCloud), identifying words with the biggest contribution in Sentiment , identifying words in Positive Sentiment, negative sentiment and neutral sentiment
10. Split Data : For training and testing
11. Modeling : Here in this step ,for the hackathon

I only used **TFIDVectorizer**(Term frequency Inverse document frequency (TFIDF) is a statistical formula to convert text documents into vectors based on the relevancy of the word) and **Multinomial Naive Bayes Classifier** (probabilistic classifier to calculate the probability distribution of text data, which makes it well-suited for data with features that represent discrete frequencies or counts of events in various natural language processing (NLP) tasks) as a pipeline 


**nb_pipeline = make_pipeline(TfidfVectorizer(), MultinomialNB())**


**RESULTS ARE AS FOLLOWS:**
Multinomial Naive Bayes Classifier:
              precision    recall  f1-score   support

    negative       0.83      0.75      0.79      1721
     neutral       0.98      0.22      0.37      1244
    positive       0.73      0.96      0.83      3583

    accuracy                           0.77      6548
   macro avg       0.85      0.65      0.66      6548
weighted avg       0.81      0.77      0.73      6548

But in this project i have included 2 more pipelines

1. **svc_pipeline = make_pipeline(TfidfVectorizer(), SVC())**
Support Vector Classifier:

              precision    recall  f1-score   support

    negative       0.90      0.88      0.89      1721
     neutral       0.91      0.91      0.91      1244
    positive       0.95      0.96      0.95      3583
    accuracy                           0.93      6548
   macro avg       0.92      0.92      0.92      6548
weighted avg       0.93      0.93      0.93      6548

3. **pa_pipeline = make_pipeline(TfidfVectorizer(), PassiveAggressiveClassifier())**
Passive Aggressive Classifier:
              precision    recall  f1-score   support

    negative       0.89      0.87      0.88      1721
     neutral       0.89      0.91      0.90      1244
    positive       0.95      0.94      0.94      3583

    accuracy                           0.92      6548
   macro avg       0.91      0.91      0.91      6548
weighted avg       0.92      0.92      0.92      6548

Out of these 3 , SVC has the best accuracy results (The Best Model is SVC : 0.93)
I will add 2 more pipelines later
**bernoulli_nb_pipeline = make_pipeline(TfidfVectorizer(), BernoulliNB())

logistic_pipeline = make_pipeline(TfidfVectorizer(), LogisticRegression())**
