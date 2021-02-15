# project_03

# Predicting Fraud/Not-Fraud in Credit Card Transactions

This effort combines large scale data analysis (over 500k records and more than 400 observation attributes) with various classification modeling techniques, including K-Nearest-Neighbors (KNN), Logistic Regression, and XGBoost, to analyze and identify the roughly 3% of fraudulent transactions present in the data set. 

## Description and Data Used

Data comes from the Kaggle Competition [Can you detect fraud from customer transactions](https://www.kaggle.com/c/ieee-fraud-detection), sponsored by the IEEE Computational Intelligence Society (IEEE-CIS) and Vesta Corporation, the world’s leading payment service company.  The data includes a mix of some categorical, but mostly numeric, fields covering information on the transaction (e.g. what type of card it was that was used, when it was used, etc.) and additional information on the "identity" associated with the card and the specific transaction, including IP addresses, information on the device used for the transaction, etc. Although there was a significant amount of data available, certain limitations, including data column titles being masked due to privacy restrictions, made interpretation of particular elements more challenging than others. Additionally, a number of fields had significant missing data, and were removed accordingly (see below). 

## Overall Outcome

*Ultimately using a dataset comprised of roughly 200 features, an XGBoost-based classifier capable of ROC AUC 94% was designed, with precision and recall at (for example, using a fraud probability threshold of greater than 30%) 80% and nearly 60%, respectively.* 

## Features and Target

* **Target:** Fraud vs Non-Fraud Classification (isFraud column). For business use case purposes, focused mostly on precision, that is ensuring that if a prediction is made it is strong, and there aren't unnecessary customer experience impacts, or additional, unnecessary work for fraud investigators.
* **Features Used:** ╸ Counts (e.g. of shared activity, shared uses of the same card); Address information (e.g. location of the purchaser, the zip code of the purchaser); other profile  information (e.g. email domain of the purchaser); time information (e.g. time since last use); device information (e.g. IP address, browser used); and features designed by Vesta corporation (e.g., how many times the payment card associated with a IP and email or address appeared in 24 hours time range). As noted, there were significant columns with missing values, so anything with greater than 70% missing data was removed.   

## Tools & Techniques Used

#### *For Data Collection and EDA:*
* Python Jupyter Notebook
* Pandas and Numpy

#### *For Classification Modeling:*
* Scikit-Learn
* K-Nearest Neighbors
* Logistic Regression
* XGBoost (with Grid Search)

## Workbooks
* Data Prep: Final compilation of data ingest, data pre-processing (including data set file pickling), and exploratory data analysis
* Project_03: Scratch workbook for initial modeling and project design
* Project_03_Logistic_Regression: Workbook for logistic regression modeling
* Project_03_KNN: Workbook for KNN modeling
* Project_03_XGBoost_Baseline: Workbook for XGBoost modeling
* Project_03_SQL_Challenges (various): Markdown and Python Notebooks for SQL challenges (NOTE: Certain questions in challenges 3 and 4 remain only partially complete as of 2/15)

## Analysis Limitations

* **Masked Data Columns and Subsequent Interpretation:** As mentioned, the masking of certain data elements, especially those from the Vesta Corporation itself, made interpretation somewhat challenging. However, by using some of the more clear cut features (e.g. card type, which was clear from the content of the field) in combination with timing metrics, for example, strong new features could be derived, and the Vesta features potentially dropped altogether in future iterations. 

## Possible Impacts & Future Efforts

The expansion of approaches fraudsters take, and the lengths they go to avoid detection only continue to increase. Leveraging an extensive data set like this, with investigators coming to understand interaction features and patterns lurking under the surface, helps the pendulum swing their way, even if only temporarily. 

#### *Future Efforts:*
The goal for this analysis is to further 'level-up' from looking for bad transactions to really focusing on bad cards, and then one layer up from there, identify those accounts which are fully compromised. While that will require some additional insight into ertain columns, those patterns and a further understanding of card-compromise will assist with further feature engineering and continued improvement in the precision score.
