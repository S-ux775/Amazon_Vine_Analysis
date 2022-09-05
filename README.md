# Amazon_Vine_Analysis

Overview of the analysis: 

The project consist of analysis of the Amazon Vine program: a service that allows manufacturers and publishers to receive reviews for their products. 

The program is a paid one and it requires for subscribers to publish a review. 

We want to determine if having a paid Vine review makes a difference in the percentage of 5-star reviews.

The process consists of:
* Chosing a dataset from AWS services

An account is opened to use AWS data and cloud services. An AWS RDS instance is set up to load data using PostgreSQL.

An AWS dataset is picked from a list provided by Amazon: Amazon Review Datasets: 

https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Beauty_v1_00.tsv.gz

**** DELIVERABLE 1: Perform ETL on Amazon Product Reviews

A new database is created with Amazon RDS using pdAmin.

Using code from challenge_schema.sql a query is run to create 4 tables in the database:

customers_table, products_table, 
review_id_table, and vine_table.

a) EXTRACT:
Using PySpark the data set is extracted into a DataFrame.

b) TRANSFORM:
The original dataset contains 5,115,666 records.

* Two colums are transformed:
star_rating to IntegerType
review_date to DateType

* Rows with null or Nan are dropped
* Duplicate rows a dropped

* Manipulate product_id to match RDS structure
The dataset is reduced to 588,771 records

c) LOAD:
Data is loaded from Colab

**** DELIVERABLE 2: Determine Bias of Vine Reviews Reviews

Using PySpark a Dataframe is created and filtered with a count of 20 or more votes (helpful_votes) and filtered again to show the ratio where helpful_votes to total_votes is equal or greater than 50%.

* RESULTS (please refer to images folder):

* How many Vine reviews and non-Vine reviews were there?
There were 647 Vine reviews (Paid Reviews)
There were 74,113 non-Vine reviews (Unpaid Reviews)

* How many Vine reviews were 5 stars?  
Paid five_star reviews: 229

* How many non-Vine reviews were 5 stars?
Unpaid five_star reviews: 43,217

* What percentage of Vine reviews were 5 stars? 
35% of 5 star reviews were paid.

* What percentage of non-Vine reviews were 5 stars?
58% of 5 star reviews were unpaid.

There is no bias in the Amazon Vine program. 

Summary: 

In the study, 58% of 5 star reviews came from unpaid suscribers whereas a lower 35% of 5 staar reviews originated from paid subscribers. Clearly, there is no bias in the Amazon Vine program. 


