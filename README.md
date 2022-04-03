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
