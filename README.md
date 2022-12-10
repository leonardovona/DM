# Data Mining 22/23

## Dataset description
The data contains information about tweets. This dataset is composed of 2 csv files:
- users.csv
- tweets.csv

In users.csv there are the following variables:
1. User Id: a unique identifier of the user
2. Statuses Count: the count of the tweets made by the user at the moment of data crawling
3. Lang: the user’s language selected
4. Created at: the timestamp in which the profile was created
5. Label: a binary variable that indicates if a user is a bot or a genuine user
  
In tweets.csv each row contains information about a single tweet. In this case the variablesare:
1. ID: a unique identifier for the tweet
2. User Id: a unique identifier for the user who wrote the tweet
3. Retweet count: number of retweets for the tweet in analysis
4. Reply count: number of reply for the tweet in analysis
5. Favorite count: number of favorites (likes) received by the tweet
6. Num hashtags: number of hashtags used in the tweet
7. Num urls: number of urls in the tweet
8. Num mentions: number of mentions in the tweet
9. Created at: when the tweet was created
10. Text: the text of the tweet
  
## Task 1: Data Understanding and Preparation

### Task 1.1: Data Understanding
Explore the dataset with the analytical tools studied and write a concise “data understanding” report assessing data quality, the distribution of the variables and the pairwise correlations.

### Task 1.2: Data Preparation
Improve the quality of your data and prepare it by extracting new features interesting for describing the user and his/her behavior derived from the information collected from the tweets.

Examples of indicators to be computed are:
- How many tweets were published by the user?
- How many tweets are published by the user in a given period of time?
- Total number of tweets
- Total number of likes and comments
- Ratio between the number of tweets and the number of likes
- Entropy of the user
- Average length of the tweets per user
- Average number of special characters in the tweets per user

Each indicator has to be correlated with a description and when it is necessary also its mathematical formulation.  
The profile will be useful for the clustering analysis (i.e., the second project’s task). Once the set of indicators is computed, explore the new features for a statistical analysis (distributions, outliers, visualizations, correlations).

#### Subtasks of DU:
- Data semantics for each feature that is not described above and the new ones defined
- Distribution of the variables and statistics
- Assessing data quality (missing values, outliers, duplicated records, errors)
- Variables transformations
- Pairwise correlations and eventual elimination of redundant variables.
  
## Task 2: Clustering analysis
Based on the user’s profile explore the dataset using various clustering techniques. Carefully describe your decisions for each algorithm and which are the advantages provided by the different approaches.

#### Subtasks
- Clustering Analysis by K-means:
  1. Identification of the best value of k
  2. Characterization of the obtained clusters by using both analysis of the k centroids and comparison of the distribution of variables within the clusters and that in the whole dataset
  3. Evaluation of the clustering results
- Analysis by density-based clustering:
  1. Study of the clustering parameters
  2. Characterization and interpretation of the obtained clusters
- Analysis by hierarchical clustering
  1. Compare different clustering results got by using different versions of the algorithm
  2. Show and discuss different dendrograms using different algorithms
- Final evaluation of the best clustering approach and comparison of the clustering obtained
- Optional: Explore the opportunity to use alternative clustering techniques in the library: https://github.com/annoviko/pyclustering/
  
## Task 3: Predictive Analysis
Consider the problem of predicting for each user the label which is a binary variable that indicates if a user is a *bot* or a *genuine* user.
1. define a user profile that enables the classification. Please, reason on the suitability of the user profile, defined for the clustering analysis. In case this profile is not suitable for the above prediction problem you can also change the indicators.
2. perform the predictive analysis comparing the performance of different models discussing the results and discussing the possible preprocessing applied to the data for managing possible identified problems that can make the prediction hard. Note that the evaluation should be performed on both training and test sets.
  
## Task 4: Time Series Analysis
Consider the tweets.csv dataset and only tweets posted in year = 2019. Extract for each user a time series representing Twitter's timeline. Compute for each day of the 2019 the following score:
$$SuccessScore = \frac{AcceptanceScore}{DiffusionScore + 0.1}$$
where:
- $AcceptanceScore = retweet\ count + reply\ count + favorite\ count$
- $DiffusionScore = num\ hashtags + num\ mentions + num\ urls$

The $AcceptanceScore$ is considered to understand how much the social network enjoys the shared content. While the $DiffusionScore$ describes the effort put on promoting the tweet by the content creator.  
Each value of the time series (one for each user) corresponds to the $SuccessScore$ for a certain day of 2019. In case a user did not post any tweets in a certain day, set the $SuccessScore = -1$.  
The goal of this task is grouping similar users through the use of the created time series and, exploiting the binary variable bot, extracting shapelets.
