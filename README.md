# amazon-fine-food-reviews
Amazon Fine Food Reviews using Machine Learning and NLP

NOTE: [Click to get dataset](https://drive.google.com/file/d/11zzpZ0YnaOVMGQSYeNtvK_In-PNsxMW1/view?usp=sharing)

## Problem Statement/Objective
Find polarity of reviews. Classifying the reviews as positive or negative.

It is a binary Classification problem.

Given a review, determine whether the review is positive(Rating of 4 or 5) or negative(rating of 1 or 2)

## Dataset

__Data Source:__[Click Here](https://www.kaggle.com/snap/amazon-fine-food-reviews)

__EDA:__ [Click Here!](https://nycdatascience.com/blog/student-works/amazon-fine-foods-visualization/),

The Amazon Fine Food Reviews dataset consists of reviews of fine foods from Amazon.

| Features | Values |
| :--      |  --:   |
| Number of reviews                    | 568,454              |
| Number of users                      | 256,059              |
| Number of products                   |  74,258              |
| Time-span                            | Oct 1999 - Oct 2012  |
| Number of attributes/Columns in data | 10                   |

__Attribute Information:__
* 1. **Id**
* 2. **ProductId** - unique identifier for the product
* 3. **UserId** - unqiue identifier for the user
* 4. **ProfileName**
* 5. **HelpfulnessNumerator** - number of users who found the review helpful
* 6. **HelpfulnessDenominator** - number of users who indicated whether they found the review helpful or not
* 7. **Score** - rating between 1 and 5
* 8. **Time** - timestamp for the review
* 9. **Summary** - brief summary of the review
* 10. **Text** - text of the review

## Objective
Given a review, determine whether the review is positive(Rating of 4 or 5) or negative(rating of 1 or 2)

__Question:__ How to determine if a review is positive or negative?
__Answer:__ We could use the Score/Rating. a rating of 4 or 5 could be considered a positive review. A review of 1 or 2 could be considered as negative. A review of 3 is neutral or ignored. This is an approximate and proxy way of determining the polarity (positivity/negativity) of a review.

## Loading the data
**The dataset is available in two forms**
* **.csv file**
* **SQLite Database**

In order to load the data, We have used the SQLITE dataset as it easier to query the data and visualise the data efficiently.
Here as we only want to get the global sentiment of the recommendations (positive or negative), we will purposefully ignore all Scores equal to 3. If the score id
above 3, then the recommendation wil be set to "positive". Otherwise, it will be set to "negative".

## Reading Data

__Sample dataset__: header of the dataset.

|Id |ProductId |UserId |ProfileName |HelpfulnessNumerator |HelpfulnessDenominator |Score |Time |Summary |Text |
|:-- |:-- |:-- |:-- |:--|:-- |:-- |:-- |:-- |--:|
|1 |B001E4KFG0 |A3SGXH7AUHU8GW |delmartian |1 |1 |1 |1303862400|Good Quality Dog Food|I have bought several of the Vitality canned d...|
|2 |B00813GRG4 |A1D87F6ZCVE5NK |dll pa |0 |0 |0 |1346976000 |Not as Advertised|Product arrived labeled as Jumbo Salted Peanut...|

## EDA(Exploratory Data Analysis)

### Data Cleaning: Deduplication
Removing duplicate reviews

## Text Preprocessing.
After finishing deduplication, we need to further preprocess the reviews before modeling.

Hence in the preprocessing phase we do the following in the order below:

1. Begin by removing the html tags
2. Remove any punctuations or limited set of special characters like , or . or # etc.
3. Check if the word is made up of english letters and is not alpha-numeric
4. Check to see if the length of the word is greater than 2 (as it was researched that there is no adjective in 2-letters)
5. Convert the word to lowercase
6. Remove Stopwords
7. Finally Snowball Stemming the word (it was obsereved to be better than Porter Stemming)


## Featurization

**We do many featurization techniques**

* **BOW: Bag of Words**
* **Bi-gram, n-grams**
* **TF-IDF: Term Frequency-Inverse Document Frequency**
* **Word2Vec**: **Average Word2Vec, TF-IDF Word2Vec**

## Machine Learning Modeling
I tried these Machine Learning Algorithms on given Featurization techniques

* __Logistic Regression__
* __Linear Discriminant Analysis__
* __K Nearest Neighbors Classifier__
* __CART: Classification and Regression Trees__
* __Multinomial Naive Bayes__
* __Support Vector Machine Classifier__


## Best Algorithm

**Logistic Regression** is the best algorithm in all the cases.
