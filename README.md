# Amazon_Vine_Analysis

"Big Market" is a startup that helps businesses optimize their marketing efforts.<br> One of "Big Markets" clients has requested some pretty hefty analytics.<br> The client "Sell-By" is about to release a large catalog of products on a leading retail website.<br> They want to know how the reviews of their products compared to the reviews of similar products sold by their competitors. They're also interested in enrolling in a program that gives out free products to select reviewers, but they want to know if it's worth the cost.

<br> As a Data Analyst for "Big Market" I was hired to harness that power of Big Data.<br> There are thousands of reviews, and they're words, not numbers, so I will  "translate" them in order to analyze them.



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
