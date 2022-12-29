# Amazon_Vine_Analysis
## Overview
### Purpose
The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Our task within the current project is to analyze Amazon reviews written by members of the paid Amazon Vine program.
### Methodology
In this project, you’ll have access to approximately 50 datasets, one of which should be picked to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. For the second part of the project, we will use PySpark to determine if there is any bias toward favorable reviews from Vine members in your dataset. 

## Results
### ETL on Amazon Product Reviews
from all the 50 datasets accaessed through the [link](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt) provided, we picked US reviews dataset for software solutions. The ETL process for extracting data from the source, it's modification and creation of tables for the normalised database can be examined in the [.ipynb file](https://github.com/ArmineKhanan/Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb) of the currrent repository.

###  Bias of Vine Reviews
1. In total there are 341931 reviews in vine_df table.
2. 153947, 45.0% of wich are 5-star reviews.
3. 32.5% and 45.4% of all 5-star reviews are paid and unpaid respectively.
From the data above (3) we can infer that the ratio of 5-star reviews is bigger in case of unpaid reviews. In other words positive feedbacks are more prbable to happen unpaid/voluntary revies.
4. 2.2% of 5-star reviews are paid, the rest 97.8% are unpaid.
The last finding (4) showcases the owherwhelming contribution of unpaid reviews to the overall amount of 5-star grades.

## Summary

To statistically prove the existance of bias the ran a statistical test.

<b>Null hypothesis:</b> There is no difference in the percentage of 5-star reviews among paid and unpaid feedbacks.

<b>Alternative hypothesis:</b> The percentage of 5-star reviews among paid feedbacks differs from the one observed for unpaid feedbacks.

To assess the truth of the Null Hypothesis we <b>delivered a Chi Sqaure test</b> and got the results presented in the image below:
<kbd><img src="https://github.com/ArmineKhanan/Amazon_Vine_Analysis/blob/main/extra_analysis.png" width="800" /></kbd>

Based on the results (low P-Value) we <b>rejected the Null hypothesis</b> and confimed that the percentage of 5-star reviews are significantly higher among paid feedbacks.


