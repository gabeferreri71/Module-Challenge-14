# Module-Challenge-14: Machine Learning Trading Bot
## Establish a Baseline Performance
### 1 - 3. These steps have already been completed, consisting of imports, importing the datato a dataframe, filtering the data, setting and generating moving averages, establishing signals, calculating and plotting strategy returns, splitting the data into test and training sets, and generating the X and y-related dataframes.
### 4. To instantiate the SVC classifier model instance, we set our svm_model variable to svm.SVC(). For fitting, we use svm_model.fit(), with internal parameters of X_train_scaled and y_train. We then predict the svm_model with .predict() and an internal variable of X_test_scaled. To review the array, we take the predicted model, svm_pred[:10].
### 5. For the classification report, we create a new variable and assign it to classification_report(y_test, svm_pred), then print the result.
### 6. For a predictions dataframe with Predicted values, Actual Returns, and Strategy Returns, we created a new dataframe, with the index set to X_test. We add the model predictions by taking the new dataframe with ['Predicted'] added, and assign it to svm_pred. To add the Actual Returns and Strategy Returns, we follow a similar process:
### predictions_df['Actual Returns'] = signals_df['Actual Returns']
### predictions_df['Strategy Returns'] = signals_df['Strategy Returns']
### We then use the display() function on the predictions_df with .head() and .tail() in use.
### 7. To plot cumulative returns, we will need both .cumprod() and .hvplot() on (1 + predictions_df]['Actual Returns','Strategy Returns']]). 
### (See evaluation report below for baseline info)
## Tune the Baseline Trading Algorithm
### See Evaluation Report below for elaboration.
## Evaluate a New Machine Learning Classifier
### 1. This will be expaned on in the evaluation report, but we decided to use the RandomForestClassifier and and created a model instance.
### 2. The model is fitted with .fit(X_train_scaled, y_train) and predicted with .predict(X_test_scaled), then reviewed. 
### 3. For the classification report, classification_report(y_test, ml_pred) followed by an input statement was assigned to a report variable. Like before, a new predictions dataframe is created with X_test set to the index. We then add the strategy and Actual Returns to the dataframe, with the Trading Algorithm Returns set to the product of the Actual and Strategy Returns. For an optimized 36 month training window (see more in evaluation), we used the loc function on the time where the Trading algorithm Returns (after the model was ran a few times) were significantly the highest, then displayed the result. Like before, we need a combination of .cumprod() and .hvplot() applied to (1+ml_predictions_df[['Actual Returns', ' Trading Alogrithm Returns']])




# Evaluation Report
## Resulting Model
![36f](https://user-images.githubusercontent.com/95319421/161433448-6f271594-8d24-4a6c-9b18-4c4223a16dc4.PNG)
### The final result of our machine learning trading bot algorithm consists of using the RandomForestClassifier, the 50 and 100 SMAs, and a training of 36 months, set from 06-25-2018 to 06-25-2021, with evaluation provided below.
## Summary 
![baseline](https://user-images.githubusercontent.com/95319421/161433562-9c9d0e47-d309-4fba-b10b-19ba68e65c07.PNG)
### Displayed above is our baseline model for the original data utilizing the 50 and 100 SMAs. When working through the accessment, the 100 SMA was held constant, with the smaller SMA getting tested at 4 (assignment default), 20, 50, and 75. The tuned results for the 20, 50 and 75 SMA vs 100 SMA can be seen below:
![20-100](https://user-images.githubusercontent.com/95319421/161433770-4d2d34bd-1292-4160-836e-4287447b7cc5.PNG)
![50-100](https://user-images.githubusercontent.com/95319421/161433784-b75f42e3-f598-4819-9bfc-00cc61776961.PNG)
![75-100](https://user-images.githubusercontent.com/95319421/161433803-59eb3b45-7b5c-4568-b2e2-1617ffa11e49.PNG)
### We preferred to modify our training window after SMA tuning to get a better visualization of what periods the Strategy model was outperforming. From this, the 36 and 48 month training seemed optimial and were tested. In testing training windows and SMA combinations, we found our highest model accuracy using the 50 and 100 SMA. Overall, the effect of modifying SMA windows is that the higher the SMAs get, the more gradual and 'smooth' the returns model appears. By limiting the training window from 48 to 36 months, we can make more precise decisions as the bot is working in a smaller time period.
![accreport](https://user-images.githubusercontent.com/95319421/161434064-88634cb8-09be-45ac-b21c-fcf4ccdf0ae3.PNG)
### Note this was our most accuracy model produced at 56%.

### In terms of machine learning classifers tested, evaluated using LogisticRegression, AdaBoost, DecsionTreeClassifier, and RandomForestClassifier. Random Forest was chosen for the model pick due to using averages to improve predictive accuracy and mitigate overfitting, which is ideal for a trading bot. Note that our tested LogisticRegression classifer model had a higher accuracy (57% as opposed to 52%), however Random Forest, in respect to all models tested, performs at the higher margin difference. Below can be seen the Random Forest classification report:
![m1acc](https://user-images.githubusercontent.com/95319421/161434594-bcdfc105-4c1a-4ca2-bee1-1539e8a62f03.PNG)


