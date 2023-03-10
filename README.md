# Amazon_Vine_Analysis
## Overview
### Purpose
The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Our task within the current project is to analyze Amazon reviews written by members of the paid Amazon Vine program.
### Methodology
In this project, you’ll have access to approximately 50 datasets, one of which should be picked to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. For the second part of the project, we will use PySpark to determine if there is any bias toward favorable reviews from Vine members in your dataset. 

## Results
### ETL on Amazon Product Reviews
From all the 50 datasets accessed through the [link](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt) provided, we picked the US reviews dataset for software solutions. The ETL process for extracting data from the source, its modification, and the creation of tables for the normalized database can be examined in the [.ipynb file](https://github.com/ArmineKhanan/Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb) of the current repository.
###  Bias of Vine Reviews
1. In total there are 341931 reviews in vine_df table.
2. 153947, 45.0% of which are 5-star reviews.
3. 32.5% and 45.4% of all 5-star reviews are paid and unpaid respectively. That is, the ratio of 5-star reviews is bigger in the case of unpaid reviews. In other words, positive feedbacks are more probable to happen in unpaid/voluntary reviews.
4. 2.2% of 5-star reviews are paid, and the rest 97.8% are unpaid. In other words, the overwhelming contribution of unpaid reviews to the overall amount of 5-star grades.

## Summary

To statistically prove the existance of bias the ran a statistical test.

<b>Null hypothesis:</b> There is no difference in the percentage of 5-star reviews among paid and unpaid feedbacks.

<b>Alternative hypothesis:</b> The percentage of 5-star reviews among paid feedback differs from unpaid feedback.

To assess the truth of the Null Hypothesis we <b>delivered a Chi Sqaure test</b> and got the results presented in the image below:
<kbd><img src="https://github.com/ArmineKhanan/Amazon_Vine_Analysis/blob/main/extra_analysis.png" width="800" /></kbd>

Based on the results (low P-Value) we <b>rejected the Null hypothesis</b> and confirmed that the percentage of 5-star reviews is significantly higher among paid feedback.


