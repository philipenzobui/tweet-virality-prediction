# Virality of Tweets using Tree-Based Models
Applying Tree-Based models to perform virality of Tweets regression as per the 2023 SOA (Society of Actuaries) / CIA (Canadian Institute of Actuaries) / CAS (Casualty Actuarial Society) joint predictive analytics competition. 

"For this competition, you will predict the engagement of (mostly) recent tweets from high-profile Twitter accounts based on fields such as blockchain, cryptocurrency, and Web3."

I chose to use tree-based models for this competition due to my experience with them, the ease of implentation (given 48h time contraint), and predictive power for irregular patterns.

I ended this competition in 6th place. Time constraints limited the extent to which I wanted to push this model. This repository contains improvements to the model made after the competition which could have resulted in a better placement.

I hope this repository can serve as inspiration and guidance for the first steps for anyone predicting Tweet virality via machine learning.

## Data

The datasets contain (mostly) recent tweets from high profile Twitter accounts in the fields of blockchain, cryptocurrency, and Web3. There are several columns to help you predict the engagement from a tweet. Engagement is defined as the number of retweets and likes and is available in the column engagement_count. There was 26,757 rows in the training set, and 8,921 in the submission set.

I have not put the data in this repository, as it is unclear whether competitors are allowed to use the data given outside of the competition.

The Tweets data contained the following information:

- tweet_id - An unique identifier for each tweet
- screen_name - The screen name of the user who tweeted
- created_at - The date and time the tweet was tweeted
- full_text - The full, unedited text of the tweet
- display_text_range - The length of the tweet
- in_reply_to_screen_name - The names of users if the tweet was replying to another tweet
- is_quote_status - TRUE if quoting another tweet
- includes_media - TRUE if the tweet includes media
- hashtags - A list of all the hashtags from the tweet
- user_mentions - The names of other users that are tagged in the tweet
- urls - URLs used in the tweet
- engagement_count - The total number of retweets and likes on the tweet

I also scrapped some user data directly from the Twitter API as allowed by the rules: "You are allowed to find external data that could potentially augment the existing dataset, however finding the actual tweets on the internet and identifying their number of likes / shares would be considered cheating." 

The scrapped data contained the following information. All this information is available publicly on the users profile. There were 1410 unique accounts, including 57 that were unique to the training set, and 9 that were unique to the test set.

- username - The screen name of the user who tweeted
- followers_count - The number of followers accounts of the user who tweeted
- following_count - The number of following accounts of the user who tweeted
- tweet_count - The total number of Tweets of the user who tweeted
- join_date - The date that the user joined Twitter
- is_verified - TRUE if the user is verified
- location - The location of the user who tweeted
- likes_count - The number of likes of the user who tweeted
- media_count - The number of media posted by the user who tweeted
- user_description - The profile description of the user who tweeted
- lists_count - The number of lists that the user who tweeted is listed on
- friends_count - The number of friends (user follows this account, and this account follows the user) of the user who tweeted

## Notebooks

This repository contains two notebooks. The [first one](https://github.com/philipenzobui/tweet-virality-prediction/blob/main/data_preprocessing_github.ipynb) contains all the data cleaning, preprocessing and feature generation. The [second one](https://github.com/philipenzobui/tweet-virality-prediction/blob/main/machine_learning_github.ipynb) contains the statistical learning and evaluation of the different models. I do not extensively present the data exploration, feature generation, and model comparation steps.

## Evaluation

The evaluation metric for this competition was the root mean squared error (RMSE). The baseline RMSE (average of target from test data) was 1234.97, the final model presented in this repository was 465.65 (62.3% improvement).
