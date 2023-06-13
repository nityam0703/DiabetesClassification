INTRODUCTION
The aim of this analysis is to investigate a range of health-related factors and their interconnections to classify diabetes accurately. These factors include aspects such as age, gender, body mass index (BMI), hypertension, heart disease, smoking history, HbA1c level, and blood glucose level. This comprehensive examination will not only provide insights into the patterns and trends in diabetes risk but will also create a solid base for further research. Specifically, research can be built on how these variables interact and influence diabetes occurrence and progression, crucial knowledge for improving patient care and outcomes in this increasingly critical area of healthcare

PREFACE
In this analysis, we have chosen the RandomForest classifier and SVM as our model. We will run both and then choose the better model fitting our data.

CLASS IMBALANCE
From the EDA ,the dataset is imbalanced (with 9% positive cases for diabetes and 91% negative cases), it's essential to balance the data to ensure that the model doesn't get biased towards the majority class. For this purpose, the Synthetic Minority Over-sampling Technique (SMOTE) is used, which generates synthetic samples for the minority class.

PREPROCESSING
Preprocessing is a crucial step before training the model. In this case, numerical features are standardized (mean removed and scaled to unit variance), and categorical features are one-hot encoded. Standardization is not required for all models but is generally a good practice. One-hot encoding is necessary for categorical variables to be correctly understood by the machine learning model.

MODEL BUILDING AND HYPERPARAMETER TUNING
We use GridSearchCV on both SVM and RandomForest to find the best parameters for our model. Due to being a large data , it was taking a lot of time to run for svm . So I randomly selected the parameters for SVM.It was running almost 405 times on more than 100000 data entries. RandomForest was quicker and for that we got the parameters.
-->max_depth=none Meaning tree went to full depths.
-->min_samples_leaf=1: This means that each leaf (the end node of a decision tree, where predictions are made) must contain at least two samples. This parameter, like max_depth, is a way to control overfitting. 
-->min_samples_split=2: This tells us that a node must contain at least two samples in order to be split (to create two child nodes). Similar to the min_samples_leaf parameter, this can help control overfitting.
-->n_estimators of 200: This is the number of decision trees in the forest. The Random Forest algorithm works by averaging the predictions of many decision trees to make a final prediction, which helps reduce overfitting and variance. In this case, it seems that having 50 trees in the forest gives us the best performance.

CONFUSION MATRIX
The trained model is evaluated on the test set. Confusion matrix is used to visualize the performance of the model. It shows the true positive, true negative, false positive, and false negative predictions of the model.
Overall we have a accuracy of 91 in SVM and 97 for RandomForest.
The confusion matrix also has a great recall,precision and f score.

SUMMARY
The analysis employed a Random Forest classifier to predict diabetes based on various health indicators and lifestyle factors. The model was trained and evaluated on a dataset of 100,000 records, and Hyperparameter tuning was performed to optimize the model's performance.

The model achieved an accuracy of approximately 97.2%, with precision of 0.98 for class 0 (non-diabetic) and 0.98 for class 1 (diabetic). It was also able to recall 96% of non-diabetic cases and 97% of diabetic cases correctly. The relatively high accuracy and balanced performance on both classes indicate that the model is well-tuned and robust.
