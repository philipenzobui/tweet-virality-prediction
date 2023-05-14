# Virality of Tweets using Tree-Based Models
Applying Tree-Based models to perform virality of Tweets regression as per the 2023 SOA (Society of Actuaries) / CIA (Canadian Institute of Actuaries) / CAS (Casualty Actuarial Society) joint predictive analytics competition.

"For this competition, you will predict the engagement of (mostly) recent tweets from high-profile Twitter accounts based on fields such as blockchain, cryptocurrency, and Web3."

## Data

The datasets contain (mostly) recent tweets from high profile Twitter accounts in the fields of blockchain, cryptocurrency, and Web3. There are several columns to help you predict the engagement from a tweet. Engagement is defined as the number of retweets and likes and is available in the column engagement_count.

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

I also scrapped some user data directly from the Twitter API as allowed by the rules: "You are allowed to find external data that could potentially augment the existing dataset, however finding the actual tweets on the internet and identifying their number of likes / shares would be considered cheating." The scrapped data contained the following information.

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




## Analysis Notebooks

See the included Jupyter notebooks for the stance classification workflow using 
ULMFit and the OpenAI transformer.

**Method 1: ULMFiT**

[ulmfit.ipynb](https://github.com/prrao87/tweet-stance-prediction/blob/master/ulmfit.ipynb): (LSTM-based approach)

**Method 2: OpenAI Transformer** 

[transformer.ipynb](https://github.com/prrao87/tweet-stance-prediction/blob/master/transformer.ipynb): (Transformer-based approach)

### Module Installation

The below sections highlight the installation steps for each approach used. 
Python 3.6+ and PyTorch 1.0.0 is used for all the work shown.

Set up virtual environment:

    python3 -m venv venv
    source venv/bin/activate
    pip3 install -r requirements.txt

Once virtual environment has been set up, activate it for further development.

    source venv/bin/activate

## PyTorch requirements
Install the latest version of ```pytorch``` (1.0+) as shown below:

    pip3 install -r pytorch-requirements.txt

## ULMFit with the *fastai* framework

This utilizes the *fastai* framework (built on top of PyTorch) to perform
stance classification. 

The notebook ```ulmfit.ipynb``` uses **v1** of ```fastai```, which has been 
refactored for efficiency and updated to move forward with future PyTorch versions (1.0+).

Install ```fastai``` as shown below:

    pip3 install fastai

## spaCy language model

For tokenization, ```fastai``` uses the SpaCy library's English language model. This has
to be downloaded manually:

    python3 -m spacy download en 

## Evaluation

To evaluate the F1 score as per the SemEval 2016 Task 6 guidelines, use the *perl* 
script given in ```data/eval/``` as shown:

    perl eval.pl -u

    ---------------------------
    Usage:
    perl eval.pl goldFile guessFile

    goldFile:  file containing gold standards;
    guessFile: file containing your prediction.

    These two files have the same format:
    ID<Tab>Target<Tab>Tweet<Tab>Stance
    Only stance labels may be different between them!
    ---------------------------
