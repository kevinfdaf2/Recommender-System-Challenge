# Recommender-System-Challenge


Language:Python 3.6


Kaggle link: https://www.kaggle.com/c/res2021/overview


There is rich semi-structured data on social media platforms. This dataset for this task is collected from an online photo-sharing social media platform Flickr. People share photos with others on Flickr and make connections (friends). The task is to recommend a list of items (photos) to each user given rich information on this social media platform.


## Data

The user-item interaction data is the main data for this challenge. This data is further split into training, validation, and test sets.


### Training data

The training dataset contains a set of interactions between users and items (photos). If a user liked a photo (e.g., click the "heart" emoji which indicates a positive engagement), then there will be a record in the dataset.
Test data. Each user is provided with a list with 100 candidate photos in the test dataset, you will need to check the candidate list and recommend the top 15 photos for each user.


### Validation data

A validation dataset that you may use to tune your model. The dataset format is similar to the Test dataset, except that the ground truth of the rating is given.
Your task is to train a recommender system and generate the outputs for the test data.


In addition to the interaction data (training data), you are also provided with the following information:


### Item information


Each photo is represented as a 256-dimensional embedding which is extracted from a pre-training deep learning framework.
User information. Each user is represented as a 256-dimensional feature representation, which is the average of the image feature representations she liked in the training data


### Social information

If two users are friends, there will be a link between two users.


Please note that the user, item, social information are optional data for this challenge. You don't have to use it. It is your own choice to determine if the information should be used or not.


## Evaluation

The metric to be used in this challenge is the Normalized Discounted Cumulative Gain (NDCG) at K, with K=15 in this task.

Brief description of NDCG can be found here. http://fastml.com/evaluating-recommender-systems/


A recommender returns some items and we’d like to compute how good the list is. Each item has a relevance score, usually a non-negative number. That’s gain. For items we don’t have user feedback for we usually set the gain to zero.


Now we add up those scores; that’s cumulative gain. We’d prefer to see the most relevant items at the top of the list, therefore before summing the scores we divide each by a growing number (usually a logarithm of the item position) - that’s discounting - and get a DCG.


DCGs are not directly comparable between users, so we normalize them. The worst possible DCG when using non-negative relevance scores is zero. To get the best, we arrange all the items in the test set in the ideal order, take first K items and compute DCG for them. Then we divide the raw DCG by this ideal DCG to get NDCG@K, a number between 0 and 1.

