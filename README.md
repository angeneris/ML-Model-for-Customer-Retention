# ML Model for Customer Retention

In this project, I will find the best model to assist Beta Bank in promoting more customer retention. Beta Bank already has a strong dataset with each observation being of one customer. The features of the dataset are all the key identifying characteristics of each customer and the target is 'Exited' - whether or not the customer has left. 

## DATASET OVERVIEW

**Original Dataset:** <br>
![image](https://github.com/user-attachments/assets/911c320f-4e01-4bba-b6e0-8cf696749037)
First feature is cut off-RowNumber 

**Features** <br>
There are many irrelevant features in this dataset that were removed before training the models

**Target**<br>

Exited — сustomer has left<br> 
0 = NO <br>
1 = YES

**Machine Learning Model:**

I'll be testing out three models for this project: Random Forest Classifier, Decision Tree, and Logistic Regression because they are simple models that work well with classification tasks.

After training each model with the user behavioral data, I'll check their quality using the test dataset.


## Approach 
Conducted exploratory data analysis (EDA) then adressed class imbalance with upsampling, applied permutation importance for feature analysis using scikit-learn, and trained Random Forest, Decision Tree, and Logistic Regression models


## Results <br>
Best Model: RandomForestModel with upsampling for minority class '1' <br>

Best method to fix class imbalance: upsampling for minority class

**Feature Analysis** 
![output_72_0](https://github.com/user-attachments/assets/536747a0-b95b-43dd-81a8-016c2b9db4ba)
Results of permutation importance revealed age to be the most influential feature in the best model, followed by
Number of Products, Is Active Member,and Balance. To understand these trends more clearly, we can view exactly what age range the customer demographics inclue. In this graph, the majority of customers exiting the bank are within the ages
around 50 years old, with the majority of customers exiting being roughly 55 years old. There is
18
also another spike at about 85 years old, though there is not much activity in this age group (80-90)
to suggest that many customers exit. This seems to be an anomaly.
The younger ages in this chart, (20-30) have the smallest amount of customers exiting, most likely
because these are the newest users. Customers began to steadily drop off at age 40.

**Final Findings:** <br>
Cross-validated F1 Score: 0.563427955304428 <br>
Best Model AUC-ROC on Test Set is: 0.8487783130556508 <br>
Best Model F1 Score on Test Set is: 0.5992865636147444 <br>
<br>

## SUMMARY

After a few simple checks to ensure that the data quality was good, I began working on the dataset users. I made a few changes to the columns and data types, then used One hot encoding to ensure that all columns had a clear, understandable data type for the machine learnign models to use. I noticed a significant class imbalance making class '1' the minority class. The good thing is that this is the class that represents the customers who have exited the bank, which is still much smaller compared to their current, active customers. 

I used three different models intitially, Decsision Tree Classifier, Random Forest Classifier and Logistic Regressor. The first two models appeared to perform significantly better than the last one, so I moved on with those two. After tryign two methods to fix the class imbalance, I was able to find the best method to be upsampling the minority class. The RandomForestClassifier model trained with upsampled data performed the best and althought the F1 score on the validation set was roughly 0.62 and the AUC-ROC, 0.85, this was not the case with the test set.

In order to find the best performing model overall, I fine tuned the parameters by performing a grid search to find the best parameters to use. Typically, doing a correlation matrix and checking dependencies should happen earlier in the process but I hadn't thought about how certain features might not be as relavant so this fine tuning of features happened later. It was beneficial to see how important these changes are to the quality of the model. After determining the most important features, I transformed the dataset and finally was able to acheive a better model overall. 

Althought the model could still be improved, it has reached the acceptable treshold and is now performing on par with the training data just as much as it does with new data. 

<br>
    
**BETA BANK Business Reccomendations**  <br>

- Key Attributes to focus on for customer retention: Customers Age, Number of Products used, Balance, Active Member.
- Focus on pursuing customers in the target age range which might be newer, younger customers. This could be an oppurtunity to rebrand or reavaluate company goals and demorgraphics. 
- Taregt the most influential products that lead to customer retention. Num of Products shows relatively high importance (0.068) so this is a key attribute to returning customers. In order to take the analysis even further, we can view what these specific products are and which products are leading. Then, the bank can take a greater focus on these profit leading products.  
- The same principle should be applied to balance as it can give clues to what demorgraphic, hollistically will be more suitable for the bank to keep
