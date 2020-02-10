# Wrangle Report

In this project, we are going to wrangle WeRateDogs twitter account data. Wrangling process includes gathering data from multiple resources, assessing data qualities and tidiness issues, cleaning data, then using this cleaned data to create interesting and trustworthy analyses and visualizations.

In gathering data procedure, we brought data from two resources as the following:

- Udacity Website
- Twitter API

From Udacity server, we download `twitter-archive-enhanced.csv` manually and import the data by using read_csv function. Then, by using python request library, we download programmatically image prediction data from Udacity server and save data in `image_predictions.tsv`. Finally, we use Tweepy library to retrieve more additional data, tweet’s retweet and favorite counts. Data from twitter API will be stored in `tweet_jason.txt` file.

## Quality Issues:

#### *_twitter archived_ data:*
- Missing values in (reply to status id, reply to user id, retweeted status id, retweeted status user id, retweeted status timestamp)
- Missing dogs stages (Some tweets don't have any dog stage, All four columns have None value doggo,floofer, pupper, puppo)
- Missing dogs names (Some dogs have no name, the dog name value of this tweets is None)
- Inaccurate dog names (a, the, an,such,quite, this...)
- You only want original ratings, so we don't want the tweets that replied to another tweet.
- Errorneous datatypes (tweet_id,in_reply_to_status_id, in_reply_to_user_id,retweeted_status_id, retweeted_status_user_id, timestamp, rating_numerator,rating_denominator)

#### *_image prediction_ data:*
- Missing data for the dog preed pridiction


#### *_additional twitter_ data:*
- Some tweets have been deleted. ex. missing API data

## Tidiness Issues:

- In twitter archived data table, The doggo, floofer, pupper, and puppo should all be in one column
- Merge three data sets twitter archived, image prediction and additional twitter data into one dataframe

Once we encounter the data qualities and tidiness issues, cleaning data phase starts. In this stage, we create a copy of each data set, then we take each issue and work to solve it by three steps, Define, Code and Test. We start with tidiness issues and then data quality issues. In `wrangle_act.ipynd` file, you will notice that missing records issues in both _image prediction_ and _additional twitter_ data sets are solved during our work in Tidiness part. After cleaning data phase complete, we reassess the data again and encounter new three data quality issues which are mentioned below:

- The following colunms p1,p2,p3, dog_type and tweet_id have wrong data type
- Some tweets don't have dog types (type value is None)
- Pictures of some tweets aren't dog pictures (tweets with rate < 8 and false NN predictions)
- Timestamp should be separated into year, month, day and time


Finally, we store the new cleaned data in `twitter_archive_master.csv` in order to use it in creating analysis and visualizations.
