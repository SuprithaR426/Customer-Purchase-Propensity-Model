# Customer-Purchase-Propensity-Model

Predicts which customers are most likely to purchase in the next 90 days, enabling sales teams to prioritize high-value accounts over cold outreach.

Tech Stack
Python XGBoost Scikit-learn Spark SQL Databricks Pandas Matplotlib

Dataset
UCI Online Retail Dataset — 541,909 transactions, 4,300+ customers (Dec 2010 – Dec 2011)

Approach
Features computed from transactions before Oct 1, 2011:
FeatureDescriptionRecencyDays since last purchaseFrequencyNumber of distinct ordersMonetaryTotal spendAvgOrderValueAverage spend per orderActiveDaysNumber of distinct purchase daysUniqueProductsNumber of distinct products bought
Target — did the customer purchase between Oct 1 – Dec 10, 2011?
Time-based holdout used to prevent data leakage.

Results
MetricValueAUC-ROC0.746Accuracy68%Customers scored3,602
Priority TierCustomersAvg ScoreAvg SpendHigh Priority1,1030.838£2,931Medium Priority1,1500.517£735Low Priority1,3490.265£466
High Priority customers spend 6x more than Low Priority.

Pipeline
Raw Data → Spark SQL Feature Engineering → XGBoost Model → Priority Tier Scoring → Spark Temp View
