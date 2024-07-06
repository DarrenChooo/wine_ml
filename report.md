# Wine Quality Data Prediction Algorithm

## Dataset Overview
- The dataset consists of 1599 rows and 12 columns.
- The last column of the dataset represents the value of wine quality which I aim to create a prediction algorithm for.
- The dataset is cleaned and I will not be doing any removal of any data.

## Key Findings

### Exploratory Data Analysis
- Most of the features' histograms are a right-skewed distribution other than features such as `Density` and `pH` where they have a normmal distribution.

###  Correlation Analysis
- The correlation analysis tells us that which features are affecting the target (Quality of wine) the most. The top 5 features are:
    - Alcohol (0.48)
    - Volatile Acidicity (-0.39)
    - Sulphates (0.25)
    - Citric Acid (0.23)
    - Total Sulfur Dioxide (-0.19)

- Going deeper, I have identified certain patterns from the features:
    - The greater the alcohol, the greater the quality
    - The lower the volatile acidity, the greater the quality
    - The greater the sulphates, the greater the quality
    - The greater the citric acidity, the greater the quality
    - There is no clear relationship between total sulfur dioxidie and the quality. However, if given a relation it would be the lower the total sulfur dioxide at a minimum of 35 units of measure, the greater the quality.

## Model Building and Evaluation
- I have built both Decision Tree Model and Random Forest Model.
- To visualise the models, I have decided to create a function to determine "Good" and "Bad" wines. Whereas the quality of >7 are considered "Good", while the quality of <7 are considered "Bad".
- The models are trained on `80%` of the dataset, with the remaining `20%` used for testing.
- The random state for the models are at `42`.

### Results (Decison Tree Model)
Accuracy: 0.8719

    Classification Report:

                   precision    recall  f1-score   support
         Bad           0.92      0.93      0.93       273
        Good           0.57      0.51      0.54        47

    accuracy                               0.87       320
    macro avg          0.74      0.72      0.73       320
    weighted avg       0.87      0.87      0.87       320

Decision Tree Confusion Matrix:

    Predicted:    Bad  Good
    Actual: Bad   255    18
           Good    23    24


### Results (Random Forest Model)
Random Forest Accuracy: 0.9000

    Random Forest Classification Report:

                    precision    recall  f1-score   support
         Bad           0.92      0.97      0.94       273
        Good           0.73      0.51      0.60        47

    accuracy                               0.90       320
    macro avg          0.82      0.74      0.77       320
    weighted avg       0.89      0.90      0.89       320

Random Forest Confusion Matrix:

    Predicted:    Bad  Good
    Actual: Bad   264     9
           Good    23    24

### Conclusion
- Accuracy: The Random Forest model has a higher accuracy as compared to the Decision Tree model.
- Precision, Recall, and F1-Score: The Random Forest model shows improved precision, recall, and F1-score, especially for the "Good" class.

Confusion Matrix:
- The Random Forest model has fewer false positives `9` as compared to the Decision Tree model of `18`.
- The Random Forest and Decision Tree model are both similar in false negatives of `23`.
- The Random Forest model is highly more accurate in true negatives `264` as compared to the Decision Tree model of `255`. However, both models are the same in true postives of `24`.

This indicates that the Random Forest model performs better overall compared to the Decision Tree model, particularly in identifying "Bad" wines.

## K-means Clustrering and Principal Component Analysis (PCA)
- I have incorporate Feature Engineering to help identify patterns and reduce the dimensionality of the dataset for better prediction. The two methods are K-means and Principal Component Analysis.
- By using K-means Clustering I was able to group the wine samples into 3 clusters based on their feature similarities.
- By using PCA I was able to reduce the dimensionality of the dataset to 2 principal components for visualisation purposes.

### Results (Decison Tree Model after Feature Engineering)
Accuracy: 0.8938

    Classification Report:

                    precision    recall  f1-score   support
         Bad           0.93      0.94      0.94       273
        Good           0.64      0.62      0.63        47

    accuracy                           0.89       320
    macro avg          0.79      0.78      0.78       320
    weighted avg       0.89      0.89      0.89       320

Decision Tree Confusion Matrix:

    Predicted:    Bad  Good
    Actual: Bad   257    16
           Good    18    29

### Results (Random Forest Model after Feature Engineering)
Random Forest Accuracy: 0.9000

    Random Forest Classification Report:
                    precision    recall  f1-score   support
         Bad           0.92      0.97      0.94       273
        Good           0.73      0.51      0.60        47

    accuracy                               0.90       320
    macro avg          0.82      0.74      0.77       320
    weighted avg       0.89      0.90      0.89       320

Random Forest Confusion Matrix:

    Predicted:    Bad  Good
    Actual: Bad   264     9
           Good    23    24

### Conclusion
- After conducting K-means clustering and Principal Component Analysis (PCA), the Decision Tree model accuracy improved. Even though the Random Forest model remains the same accuracy, it still performs better than the Decision Tree model.


Confusion Matrix:
- The Random Forest model has fewer false positives `9` as compared to the Decision Tree model of `16`.
- The Random Forest has a lot more false negatives `23` as compared to the Decision Tree model of `18`.
- The Random Forest model is highly more accurate in true negatives `264` as compared to the Decision Tree model of `257`. On the other hand, the Decisio Tree model is more accurate in identifying true positives `29` as compared to the Random Forest model of `24`.

This indicates that after conducting some featured engineering, the Random Forest model performs better overall compared to the Decision Tree model, particularly in identifying "Bad" wines. However, in identifying "Good" wines, the Decision Tree model is preferred.
