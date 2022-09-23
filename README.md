# Customet-satisfaction-rate-prediction 

This binary classification model trained on data of previous passengers predicts whether a new passenger will be satisfied or not with the services provided by the airline. Below is the step-by-step procedure to arrive at solution:

1.	Data preprocessing: 

●	Loaded the train and test data into notebook using pandas  
●	Data cleaning:
a.	Removed the two irrelevant columns ‘id’ and ‘Unnamed: 0’ from train and test data
b.	Checked for null valued rows and removed them as they were very few
●	Changed the datatype of column ‘Arrival Delay in Minutes’ float to int.

2.	Exploratory data analysis:

●	Used Count plot to check whether the data is class imbalanced. Didn’t found any major imbalance hence there’s no need to tune threshold for predictions in the ML model.
●	Plotted a heatmap to check correlation between the features in the dataset. Removed the feature ‘Departure delay in Minutes’ as this feature was highly correlated with the feature ‘Arrival delay in Minutes’ with a correlation of 0.97.
●	Plotted boxplots of numerical features to visualize outliers. Removed data points that were outside the range (Q1 - 1.5 * IQR, Q3 + 1.5 * IQR) where Q1 and Q3 are first and third quartile of data respectively. 

3.	Feature engineering: Encode the categorical features with textual values into numerical values for so that machine learning algorithm can process these features.

4.	Model selection and evaluation: 

i)	Logistic regression:
•	Since logistic regression is a linear model and linear models perform better when data is normalized. Hence, we normalized the features using Standard Scaler technique which makes mean of features as 0 and standard deviation as 1.
•	The cases where model predicts satisfied, but the customer was not satisfied should be as minimum as possible to improve customer experience. Hence, we need to minimize false positives in the predictions. Hence, we chose those set of parameters that maximize the precision score of predictions. 
•	The metric we chose for evaluating the model was accuracy score defined as: Correct predictions/ Total predictions
•	The model we trained was having pretty good precision score of ~86.5%. Also, the training and testing accuracy were both ~87% respectively, which means that our model was not overfitting.




Next, we explored more and tried Random Forest Classifier because:

1.	It makes use of ensemble learning.
2.	It does feature selection on its own
3.	It doesn’t assume any linear relationship between dependent and independent variables. 


ii)	Random forest classifier:
•	Just like the above logistic regression model, we chose those set of parameters that maximize the precision score of predictions and the metric of evaluation was chosen to be accuracy score.
•	The model we trained was having precision score of ~97% and the accuracy score on testing data was ~97%. Also, the training and testing accuracy were both comparable with each other hence no overfitting was there. 

Hence, we chose the Random Forest classifier as our final model for making predictions.
