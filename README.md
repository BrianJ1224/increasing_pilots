# "## Project 3: Web APIs & NLP"
#### Author: Brian Jankowitz
[Medium](https://medium.com/@JankowitzB) | [LinkedIn](https://www.linkedin.com/in/brian-jankowitz/)

#### [Project Presentation](presentation.pptx)
#### [Jupyter Notebook](/code/project_notebook.ipynb)

## Problem Statement

With the mandatory retirmemnt age of airline pilots being 65 years old, a lot of airline pilots are reaching the mandatory retirment age. According to CNBC, there will be a demand for 800,000 new airline pilots over the next 20 years. Ex-CEO of Boeing, Dennis Muilenburg, says that "the global pilot shortage will be one of the biggest challenges facing the airline industry.

Airlines have tried to help train new pilots by creating Cadet Programs. The marketing team in our company wants to market cadet programs to people interetsed in aviation. To predict accurately which group they should market to, the marketing team wants to see from certain posts which category a user might belong to, Technology or Flying, and market to them. These two groups were chosen as they both have potential interests at becoming pilots. Different ads will be used to market to them in order to expose them to the cadet program. The ultimate goal of having them sign up for cadet programs to reduce help employ pilots at an airline. 

## Executive Summary

I decided to collect data from two subreddits, Technology and Flying. After I gathered the data and saved it to a dataframe, I analyzed the shape and the type of data that was in there. There were nulls in the data but that did not affect me cleaning the data as they were not in the two columns we were looking at.

I made a function that cleaned the data. The function makes all the characters lowercase, removes punctuation, whitespace, and html special entities, and lemmatized all the words. I then made a function to get the common words. This function prints the top 20 most common words. This was used to see which words were common. I decided to remove the common English stop words, flying, and technology as I wanted to make accurate predictions without having the name of the subreddit category in the data.

I made two models, each being tested with two vectorizers for train test split. I used Logistic Regression and MultinomialNB for my models and Count Vectorizer and Tfidf Vectorizer for my vectorizers. When the best model which had MultinomialNB and Count Vectorizer, I looked at the best ngram range and the max features. The best ngram range was (1,2) and max features was 1280. I tested max features, stop words, and ngram range. The goal was to have the least number of true negatives with a high true positive. This model had the lowest false negatives with 44 and true positive at 409. The train score was 93 and .89. There is a little overfit but this model had the least true negatives which is good for the marketing team as they won’t market to people that are not their target audience.

## Model Selection

The train and test score are overfit as there is a .04 difference. The cross val score shows us that it is very close to the test score. The best model is Logistic Regressresion with Cross Vectorizer. The way that I made the train score increase and decrease false positives was by looking at the max features and adjusting it. We adjusted it accordingly with the best estimator. Cross validation was looked at to make sure our model was doing well We have a true positive of 409 which we want to maximize and false negative of 44 which we want to minimize. It is important to have a higher true positive than false negative but it is more important to have less false positive as we don't want to waste money marketing to people who are not in the correct category This is good as it predicts the most number of true positives and the least number of false negative. This would let the marketing team market to the incorrect people which could waste their money as they would be marketing to the wrong group.

## Conclusions

We are able to predict which subreddit a person comes from 89% correctly, we can confidently say that we can differentiate between the two subreddits, flying and technology. We have a sensitivity of 97% which means we are prediciting our true positives, the subreddit that the person comes from, correctly 97%. This is good as we want to maximize the number of people that the marketing team can use to market to the their audience from each subreddit. This can help increase awareness about the cadet program with the ultimate goal of having people sign up for the cadet program. This will be able to help decrease the shortage of airline pilots in the future.

## Recommendations

I would recommend taking this model and starting with a small group to market to. If there is a higher response rate, I would increase the market spending.

## Sources

- https://bearylogical.net/post/ml-subreddit/#pipeline-for-logistic-regression-baseline
- https://github.com/amreshsharma/Machine-Learning/blob/master/NLP/Twitter%20Sentiment%20Analysissentiment_twitter_analysis.py
- James Hampton, GA Seattle
 - He gave advice how to solve certain problems
- Alanna Besaw, GA Seatltle
 - She gave advice how to solve certain problems
