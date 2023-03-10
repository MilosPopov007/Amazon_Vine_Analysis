# Amazon_Vine_Analysis

"Big Market" is a startup that helps businesses optimize their marketing efforts.<br> One of "Big Markets" clients has requested some pretty hefty analytics.<br> The client "Sell-By" is about to release a large catalog of products on a leading retail website.<br> They want to know how the reviews of their products compared to the reviews of similar products sold by their competitors. They're also interested in enrolling in a program that gives out free products to select reviewers, but they want to know if it's worth the cost.

<br> As a Data Analyst for "Big Market" I was hired to harness the power of Big Data.<br> There are thousands of reviews, and they're words, not numbers, so I will  "translate" them in order to analyze them.



![This is an image](https://github.com/MilosPopov007/Amazon_Vine_Analysis/blob/main/Resources/Amazon_Vine.png)

## Results:

What is Amazon Vine?<br>
Amazon Vine is an invitation-only program which selects the most insightful reviewers in the Amazon store to serve as Vine Voices.<br> Vine Voices have the unique opportunity to order items free of charge and share their product experiences with Amazon customers to help them make informed buying decisions.

How does it work?<br>
Once enrolled in Vine, Voices may request products from thousands of brands selling in the Amazon store which are shipped to their doorsteps at no cost.<br> They then use the products and provide insightful reviews that reflect their honest and unbiased opinions - positive, neutral, or negative. Reviews of a product ordered through Vine appear in the same location as other reviews.<br> Amazon Vine reviews are distinguished with this special badge "Vine Customer Review of Free Product" for full transparency.
Thousands of products from all types of categories are added daily, ensuring that Voices always have something new to try!<br>
Customers who consistently write insightful reviews are most likely to be invited.<br>To stay in the program, they are expected to share honest and unbiased reviews.

I will use PySpark to determine if there is any bias toward favorable reviews from Vine members in Amazon Review datasets. (US_Camera_reviews will be used)  https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt 

[Perform ETL on Amazon Product Reviews using Pyspark](https://github.com/MilosPopov007/Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb)
* First step will be creating  AWS RDS database with tables in pgAdmin
* Extract the dataset https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Camera_v1_00.tsv.gz into a DataFrame in Pyspark
* Transform the DataFrame into four separate DataFrames that match the table [schema](https://github.com/MilosPopov007/Amazon_Vine_Analysis/blob/main/challenge_schema.sql) in pgAdmin
* Transform the data
* Connect to an AWS RDS instance, and load the transformed data into pgAdmin
* Using PySpark, to determine if there is any bias towards reviews that were written as part of the Vine program


![This is an image](https://github.com/MilosPopov007/Amazon_Vine_Analysis/blob/main/Resources/Amazon_spark.png)


[Bias of Vine Reviews](https://github.com/MilosPopov007/Amazon_Vine_Analysis/blob/main/Vine_Review_Analysis.ipynb)<br>

For this analysis using PySpark, we will determine if having a paid Vine review makes a difference in the percentage of 5-star reviews
* Filter the data and create a new DataFrame to retrieve all the rows where the total_votes count is equal to or greater than 20 to pick reviews that are more likely to be helpful
* Filter the new DataFrame created in Step 1 and create a new DataFrame to retrieve all the rows where the number of helpful_votes divided by total_votes is equal to or greater than 50%
* Filter the DataFrame  created in Step 2, and create a new DataFrame that retrieves all the rows where a review was written as part of the Vine program (paid)
* Filter the DataFrame  created in Step 2, and create a new DataFrame that retrieves all the rows where a review was not part of the Vine program (unpaid)
* Determine the total number of reviews, the number of 5-star reviews, and the percentage of 5-star reviews for the two types of review (paid vs unpaid)

![This is an image](https://github.com/MilosPopov007/Amazon_Vine_Analysis/blob/main/Resources/vine_df.png)

#### Analysis Results : 
*  Number of paid reviews for Vine program was ( 233 )  vs. ( 14468 )   Number of unpaid reviews for Non Vine program 
*  5-star reviews for Vine program (paid) was ( 103 )  vs. ( 7868 )   5-star reviews for non Vine program (unpaid)
*  Percentage of 5-star reviews for Vine program (paid) was   ( 44.21  %  ) vs. ( 54.38 % ) Percentage of 5-star reviews for Non Vine program (unpaid)


### Summary:
* In the Analysis, the main focus was on the five star reviews. The goal  was to determine if there is a  Bias towards five star reviews,  made by Vine paid members. In other words, I wanted to determine if being paid by Amazon will encourage customers to give more positive reviews vs. ordinary  Amazon customers.<br> Looking at the results, Percentage of 5-star reviews for the Vine program (paid)  (44.21  %) vs. (54.38 %) Percentage of 5-star reviews for the Non Vine program (unpaid) we can conclude that there is No Bias towards positive reviews from Vine members.<br> Vine program did not have any influence on customer review results.
* If we take Amazon_Reviews_US_Camera FULL DATASET (Total number of reviews: 1801974) we will get the similar results, Percentage of 5-star reviews for the Vine program (paid) was   (41.77  %) vs. (59.05 %) Percentage of 5-star reviews for the Non Vine program (unpaid).
* In order to get more clear picture of the Amazon Vine program, I suggest to perform similar analysis on more data sets from  https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt  (approximately 50 datasets) and make a final conclusion on Amazon Vine Bias Hypothesis.

![This is an image](https://github.com/MilosPopov007/Amazon_Vine_Analysis/blob/main/Resources/vine_total.png)
