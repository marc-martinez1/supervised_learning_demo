# Credit Risk Classification

## Overview of the Analysis

The purpose of this analysis is to train a logistic regression model designed to predict the creditworthiness of borrowers utilizing historial data regarding their lending activity. Along the way we will use various techniques to train and evaluate models with imbalanced classes.

The following data was collected for our purposes:
* Loan Size
* Interest Rate
* Borrower Income
* Debt to Income Ratio
* Number of Accounts
* Derogatory Marks
* Total Debt

As well as the loan approval status, approved or denied, we will use as the testing variable for our model. This is because we wish to use the above indicators to predict which type of loan application should be approved and which should not.

In our analysis we used variables such as 'value_counts' to determine key features that could influence our models. Utilizing value_counts we found that the overwhelming majority of loans(75,036) were approved compared to only(2500). Later in our analysis, we will make changes to correct for the data sets lack of high-risk loans data to further improve our model.

The large majority of our analysis centers around the stages of the machine learning process and how we get from our initial data to a workable data set from where we can the train a Logistic Regression model. The following steps were taken:

1. Preprocessing

This step included reading in the initial data from a csv file located in our 'Resources' folder followed by seperating data into label sets 'y' which included the loan status column, and 'X' which included the remaining features needed to produce the model. From here we imported the train_test_split module from sklearn and then split the data into 'X_train', 'X_test', 'y_train', and 'y_test'.

2. Creating a Logistic Regression Model with the Original Data

Next, we began to use our preprocessed data produced from the previous step to fit a logistic regression model. First, we imported the logistic regression module from sklearn then instantiated the logistic regression model and assigned the equation to our 'model' variable. From here we fit the model and produced our prediction.

3. Creating a Logistic Regression Model with Resampled Training Data

Folowing up on our last step, we wanted to build on our previous model and refine the dataset to produce a more accurate model. This began with importing the random over sampler module from imblearn which would all us to resample the data to have an equal number of data points in regards to good loans and high-risk loans. This was done by instantiating the model, fitting the original data, and asigning the results to our 'X_resampled' and 'y_resampled' variables. From there we confirmed that the distinct values from the resampled labels data were equivalent then reinstantiated a new logistic regression model to continue our analyis. We the repeated the process detailed in step 2 to create our model.

4. Evaluating the Models' Performances

Lastly, to evaluate the performance of our original and resampled models, we calculated the accuracy scores, generated a confusion matrix, and printed a classification report. This was all done by simply calling on the 'balanced_accuracty_score', 'confusion matrix', and 'classification_report_imbalanced' functions to review our results which we will review in the following section.

## Results
-------------------------------------------
* Machine Learning Model (Original Data):
  * Balanced Accuracy Score: 0.95
  * Precision:
      * Healthy Loan: 1.00
      * High-Risk Loan: 0.85
  * Recall: 
      * Healthy Loan: 0.99
      * High-Risk Loan: 0.91
-------------------------------------------
* Machine Learning Model (Rebalanced Data):
  * Balanced Accuracy Score: 0.99
  * Precision:
      * Healthy Loan: 1.00
      * High-Risk Loan: 0.84
  * Recall: 
      * Healthy Loan: 0.99
      * High-Risk Loan 0.99
-------------------------------------------
## Summary

Based on the results, it is our belief that the machine learning model trained on the rebalanced data performs the best. However, depending on the goals of the firm, there may be instances where the original model will be preferred if the .01 increase in precision for identifying high risk loans proves more profitable against the the .08 increase in recall for identifying high risk loans since performance on healthy loans is virtually the same. The decision will ultimately be a trade off on is the .01 inrease in risk worth the .08 increase in catching healthy loans more or less favorable than the alternative. An argument could also be made to not depend on either model since some may regard 15-16% of high-risk loans being approved to be too risky for the firm.