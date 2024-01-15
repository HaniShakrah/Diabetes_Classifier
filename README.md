# Diabetes Classifier

## Data
Data sourced from years 2018-2022 of CDC's annual Behavioral Risk Factor Surveillance System survey ([BRFSS](https://www.cdc.gov/brfss/annual_data/annual_data.htm)) 


## Survey Limitations

Survey is conducted only in the United States and surrounding islands. There may be underlying phenomena that may have to do with specific geographic or cultural conditions that affect the results. Caution should be taken before generalizing to other countries and continents. 

The only method of contact interviewers use is a phone call (landlines and cell phones) with Random Digit Dialing (RDD) techniques. Certain demographics may be hard to contact and introduce bias into the results. 

Recall bias – difficulty remembering, inaccuracy in responses due to forgetting of details

Selection bias – only English and Spanish speakers 

## Dimensionality Reduction

Out of the hundreds of attributes available from the surveys, only ~35 were kept and deemed potentially important. These attributes can be seen on the project design report and includes basic demographics, physical/mental health, healthcare access, lifestyle, and more. Correlation analysis caused 3 columns to be dropped to prevent multicollinearity. Principal Component Analysis allowed us to see the cut off point where explained variance levels off and gave the number of principal components to keep to accurately capture the essential information of the data.

## Resampling

A major issue during this project was tackling the class imbalance. There was an overwhelming majority of respondents that do not have diabetes. This initially resulted in models that preferred to simply give a negative diagnosis for most individuals, since that would achieve a high accuracy. However, this defeats the purposes of the project, which is to build a robust model that can capture the relationship between the dependent and independent variables. 

Undersampling was performed to reduce the number of samples in the training set in the negative class to equal the amount in the positive class. Oversampling was also executed, using SMOTE, to synthetically create samples in the minority class to balance out the count in each class. 

## Analysis

After running many models, with different resampling techniques and hyperparameters, the best performance on the validation set came when implementing a Random Forest classifier with max depth of 30, criterion of gini, and classification threshold of 0.4. This yielded an 88% recall, 78% F1-score, and 83% AUC. 

Recall was given more emphasis because false negatives (predicting an individual to not have diabetes) are more costly than false positives (predicting an individual to have diabetes when they do not). A high F1-score shows that both recall and precision are at a reasonable level. An AUC of 0.83 suggests the model has a strong ability to distinguish the negative class from the positive class.


