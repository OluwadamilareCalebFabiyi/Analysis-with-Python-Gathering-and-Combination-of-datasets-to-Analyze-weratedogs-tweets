# Analysis-with-Python-Gathering-and-Combination-of-datasets-to-Analyze-weratedogs-tweets
# PROJECT : Developing Trustworthy Analysis and Visualizations with @weratedogs tweets.
# DATA WRANGLING REPORT
## 1) DATA GATHERING
The data was gathered using three different methods
### METHOD 1( Downloading files) - Loading directly downloaded CSV using pandas ( We Rate Dogs twitter archive)
The data was downloaded from udacity website where it came in a csv format.

The data was then loaded into pandas dataframe.

### METHOD 2 (Web Scraping) - Programmatically downoading a tsv file using requests library ( Image Predictions )
The data was downloaded using the python request library and saved into a file.

The downloaded data was in a tsv format and it was loaded into a pandas dataframe.

### METHOD 3(APIs) - Querying twitter API for each tweet's retweet and favorite count (likes) using each tweet's ID.
I could not get my developer account approved so i didnt use my twitter keys to access the APi.

I downloaded the json file which i would have gotten from twitter from udacity clasroom.

The data was read line ny line, where each line represents a tweet and it was loaded into a pandas dataframe.

## 2) DATA ASSESSMENT
The datasets were assessed Visually when viewed in excel notebok, and the datasets were assessed programatically using pandas methods.

The datasets were assessed for both quality and tidyness issues and the issues observed were documented.

#All Issues Observed

## Quality

### twitter_archive

There are some denominators that are greater than 10.- Validity

There are some numerators are far greater than 10. - Validity

The majority of values in the retweets columns are null- Completeness

The majority of values in the reply columns are null- Completeness

There are some tweets assigned to mutiple dog stages. - Quality

There are some dogs with name shown as 'a' or 'an'. - Accuracy

The tweet id is in integer form and not string - validity

### df_predict

Some tweets have all the image predictions false for a breed. - Completeness

The tweet ID column was sorted in ascending order which is not consisitent with the twitter archive table.- Consistency

The tweet id is in integer form and not string. - validity

The real dog breed should be extracted from the three predictions. - Completeness

### df_engage

There were some rows in the favorite_count column that had 0 count and that is likely impossible for a post with so much retweet_count. - Accuracy

The tweet id is in string form and not integer. - validity

## Tidyness
### twitter_archive

All rows with retweets and replies are not needed as part of our analysis.

All columns apart from text, rating_numerator, rating_denominator, name, doggo, floofer, pupper, puppo are not needed for our analysis.

The dog classification should just be one column( doggo, puppo, pupper or floofer.)

This row should be joined with image predictions and engagement to give just one table.

### df_predict

Only tweeet_id and the predicted_breed are necessary in this table.

This table should be joined with twitter_archive and engagements to give one table.

### df_engage

All the rows with reply, retweets and quoted tweets are not necessary for analysis.

Apart from the tweet id, favorite_count and the retweet count column, all other columns are redundant and should be removed.

A column that cumulates the total engagements should be in the table

The table should be joined to the twitter archive and the image predictions to make just one table.

# 3) DATA CLEANING
A copy of all datasets was created and used for the cleaning.

## QUALITY
### twitter_archive
There are some denominators that are greater than 10.- Validity
Solution

All rows with denominators greater than 10 were removed from the dataset.

There are some numerators are far greater than 10. - Validity
Solution

The numerators far greater than 10 were investigated to be for exceptional dogs and they were left.

The majority of values in the retweets columns are null- Completeness
Solution

The retweets are not needed for our analysis so we dropped the columns.

The majority of values in the reply columns are null- Completeness
Solution

The replies are not needed for our analysis so we dropped the columns.

There are some tweets assigned to mutiple dog stages. - Quality
Solution

The text was investigated for the correct stage and the correct stage were imputed.

There are some dogs with name shown as 'a' or 'an'. - Accuracy
Solution

The dogs with a or an as names were changed to Unknown.

The tweet id is in integer form and not string - validity
Solution

The tweet_id was changed to string datatype.

### df_predict
Some tweets have all the image predictions false for a breed. - Completeness
Solution

Tweets that had all predictions false were removed from the dataset.

The tweet ID column was sorted in ascending order which is not consisitent with the twitter archive table.- Consistency
Solution

The tweet_id was resorted to be in descending order.

The tweet id is in integer form and not string. - validity
Solution

The tweet_id was changed into string datatype.

The real dog breed should be extracted from the three predictions. - Completeness
Solution

The breed prediction wit the highest confidence interval was assumed to be the correct dog breed.

### df_engage
There were some rows in the favorite_count column that had 0 count and that is likely impossible for a post with so much retweet_count. - Accuracy
Solution

The rows with 0 favorite_count were retweet, replies and tweet_quotes so they were totally removed from our analysis.

The tweet id is in string form and not integer. - validity
Solution

The tweet_id was changed from integer into string datatype.

## TIDYNESS
### twitter_archive
All rows with retweets and replies are not needed as part of our analysis.
Solution

All rows with retweets and replies were removed from the dataset.

All columns apart from text, rating_numerator, rating_denominator, name, doggo, floofer, pupper, puppo are not needed for our analysis.
Solution

All the unecessary columns were dropped from the dataset.

The dog classification should just be one column( doggo, puppo, pupper or floofer.)
Solution

The dog classification was collapsed into one column.

This dataset should be joined with image predictions and engagement to give just one table.
Solution

All datasets were merged into a master dataset.

### df_predict
Only tweeet_id and the predicted_breed are necessary in this table.
Solution

All the unnecessary columns were removed from the dataset.

This table should be joined with twitter_archive and engagements to give one table.
Solution

All datasets were merged into a master dataset.

### df_engage
All the rows with reply, retweets and quoted tweets are not necessary for analysis.
Solution

All the rows with replies and retweets were removed from the dataset.

Apart from the tweet id, favorite_count and the retweet count column, all other columns are redundant and should be removed.
Solution

All redundant columns were removed from our analysis.

A column that cumulates the total engagements should be in the table.
Solution

The total engagements column was calculated by adding the favorite_count and the retweet_count.

The table should be joined to the twitter archive and the image predictions to make just one table.
Solution

All the datsets were joined together to get a master datset.

# 4) DATA RE-ASSESSMENT
All the datasets wewre re-aasessed to confirm if they were properly cleaned.

All the datsets were observed to be clean

# 5) DATA STORAGE
The gathered, assessed, and cleaned master dataset was saved to a CSV file named "twitter_archive_master.csv".
