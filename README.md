# Financial-Sentimental-Analysis
## **Objective**
Need to get sentiment analysis of financial statements and gauge its impact i.e. positive, negative or neutral on the business and government.
## **Dataset Information**
- The dataset contain a collection of financial news articles and other textual data related to the financial industry.
- The dataset contains labeled data, which is classified as positive, negative, or neutral sentiment, allowing for the training of machine learning models.
- It consists of 5842 rows and 2 columns (Sentence and Sentiment)
## **Steps Involved**
### **Data Preprocessing**:
Checked for the duplicated rows and dropped those 6 duplicated rows from the data. Found 514 duplicated sentences with different sentiments. So dropped and segregated 1028 rows from the dataset and calculated the polarity scores. Also found that only the negative and neutral data is the issue here and only these sentiments have been duplicated. From the calculated Polarity Scores there is a conclusion that the polarity scores less than zero can be classified as the 'negative' sentiment and equal to zero can be concluded as 'neutral' statements. But the statements with polarity score greater that zero cannot be concluded as 'positive' sentiments as the duplication of data is more for neutral and negative sentiments. So made an assumption that the statements having positive polarity scores are also negative in the sense of nature and hence the statements with polarity scores other than zero are to considerd as 'Negative' sentiments and concatenated this dataframe with the original dataframe.
### **Exploratory Data Analysis**:
- Created Donut chart for Sentiment data and found that most sentences are with neutral sentiments
- Created WordCloud and found that there are many links, currency names, many years, measurements (units), organization names and country names and share values in the text that does not influence the data. So they can be removed in further Text Preprocessing step 
- Created 3 other wordclouds for each sentiment separtely after preprocessing by using the analysis of above wordcloud and used the analysis of this wordcloud for furthur tokenization and lemmatization
- Performed Bigram analysis and found most repeating bigram words are found to be currency or share names and words denoting the periodical specifications and these are to be removed
- Performed Trigram analysis and inferred that the trigram analysis also shows the similar inference form the bigram analysis that most of the words are common english words and currency and some period related terms which do not contribute to the sentiments
- Created a histogram for Polarity Score in Sentences, Sentences with negative polarity will be in range of [-1, 0), neutral ones will be 0.0, and positive reviews will have the range of (0, 1)
### **Text Preprocessing**:
- from inferences by the analysis from EDA, the next step is to remove them by adding those words to 'stopwords'
- After removing those stopwords, then sentences are tokenized and lemmatized for model building
### **Model Building**:
- Categorized into Imbalanced data (without SMOTE) and Balanced data (with SMOTE)
- Carried out two types of vectorizations TF-IDF and Word2Vec for both the categories
- Used 3 models- Support Vector Machine (SVM), Random Forest and Multinomial Naive Bayes for TF-IDF vectorization for both categories
- Used 2 models- XGBoost (extreme gradient boosting) and Random Forest for Word2Vec vectorization for both categories
### **Model Evaluation**:
- Collected the training and testing scores for all the above models and evaluated them
- By comparing all the models it is found to perform well in the training dataset but the testing accuracy is not at a good level
- When compared scores for imbalanced data and balanced (SMOTE) data, Random Forest model produced more accuracy score for both TF-IDF and Word2Vec vectorization
- But after SMOTE, Random forest model is well performing in Tfidf model and gave the accuracy 1
- So finalizing the Random Forest Model with Tf-idf vectorizer is the best accuracy model
