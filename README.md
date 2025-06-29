## Project Description
This project aims to predict dropout rates for specific demographic groups and identify which ones are at higher risk given 117k records collected from the New York State Education Department (NYSED), as of 2024.

## Context
Each record represents one of 24 unique demographic groups. A record includes information such as the number of students enrolled, their graduation cohort, the institution's subtype, and a Needs/Resource Capacity (N/RC) category assigned by NYSED. The N/RC is calculated based on a poverty measure and a combined wealth ratio.


## Core Competencies Exercised
- Data Collection/Preprocessing
- Exploratory Data Analysis
- Statistical Analysis
- Supervised Machine Learning using scikit-learn 
    - Linear Regression
    - Artificial Neural Network
    - Regression Tree
- MLOps with MLflow

## Discussion
Exploratory Data Analysis reveals that Urban-Suburban students, and disadvantaged populations (Migrant, English Language Learners, Foster Care, and Homeless) are all at a higher risk of dropping out and contributes to a low linear relationship. Furthermore groups with a higher enrollment count are less likely to drop out. 

### Statistical Interpretation
Linear Regression Summary reveals the effect of features (key drivers listed below) and that they are statistically significant using the standard 95% confidence interval and also supporting our null hypothesis.

- The Migrant demographic increases the Dropout percent by 24% when compared to the "All Students" demographic.
- The "English Language Learner" demographic increases the Dropout percent by 10% when compared to the "All Students" demographic.
- Urban Suburban High needs institutions increase dropout percent by 4.07% when compared to Average needs institutions.
- The "Parent in Armed Forces" demographic decreases the Dropout percent by 5.26% when compared to the "All Students" demographic.

**The above findings are true holding all other features constant.*

### Model Evaluation
To replicate an MLOps consideration of model building and tracking, MLflow's Model Evaluatoin was utilized. Below is a screenshot of the final run results to guide our analysis and prediction power. 

Considering the low R-squared value (0.16), which suggests a lack of linearity, we expect linear regression to perform poorly. Therefore, we also implement a regression tree and a neural network, which do not assume a linear relationship between features and the target.

With the relatively similar performance in all areas the Root Mean Squared Error (RMSE) was used as the deciding factor for best model. The 8.35 RMSE tells us that the Neural Network predections are innacurate by that percentage. Considering 95% of records fall within the 0-20% dropout rate this margin of error is too large for accurate predictions. 

![alt text](assets/mlflow_graphs.png)

## Final Conclusion
These findings are consistent with the intuition that disadvantaged populations, and smaller more niche groups are at higher risk of dropping out. 

As far as predicting power it is not advised to use any of these models. However with additional features these models are promising for future development. They could also be used as a risk indicator, categorizing the result into tiers in order to generalize the anticipated dropout percent. 

## Fun Additions
When evaluating the `.summary()` function of the linear regression for coefficients and statistical relevance it is difficult to tell what category was used as the baseline for comparison of categorical variables. This task was made easier by creating a function `find_baseline(column_name)` to see what category the model used as the baeline to compare others to.

## LLM Disclaimer
The vast majority of this work is strictly derived from my understanding of the topics discussed but ChatGPT was used to streamline some aspects of this project minimally. 