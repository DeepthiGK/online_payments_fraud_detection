# online_payments_fraud_detection

## Introduction:
Every year there are millions of online payment fraud victims, and the costs for the companies can be huge. Being able to develop a fast and reliable fraud detection system can change drastically the financial performance of the business, and such a system heavily relies on historical data to understand how fraud works and be able to prevent it.

### Why online payments are the target?
Online payments are a prime target for fraudsters as such payments only need the details which are stored digitally. It’s also easier to get away with it, because it’s so much harder for the seller to verify who is really making the purchase.

## Research question:

1.  What type of online payments are the victims of fraudulent payment?
2.  What is the nature of a fraud online payment?
3.  What are the important features to detect fraudulent online payment?
4.  As fraud transactions are rare as compared to legitimate transactions so the dataset is naturally imbalanced. How to mitigate this problem?
5.  Comparison of performance of various supervised classification models and finding which model gets maximum benefit after target classes are balanced? 

## The Data:

The [Online Payments Fraud Detection Dataset](https://www.kaggle.com/datasets/rupakroy/online-payments-fraud-detection-dataset) is downloaded from [kaggle](https://www.kaggle.com/datasets). 
The table contains 11 columns, that is 10 features with a target variable 'isFraud'.
isFraud = 1 implies Fraud transaction/payment and isFraud = 0 implies legitimate transfer/payment.

## Data dictionary:

1.  *step:* represents a unit of time where 1 step equals 1 hour

2.  *type:* type of online transaction

3.  *amount:* the amount of the transaction

4.  *nameOrig:* customer starting the transaction

5.  *oldbalanceOrg:* balance before the transaction

6.  *newbalanceOrig:* balance after the transaction

7.  *nameDest:* recipient of the transaction

8.  *oldbalanceDest:* initial balance of recipient before the transaction

9.  *newbalanceDest:* the new balance of recipient after the transaction

10. ***isFraud:*** fraud transaction is our **target variable**
11. *isFlaggedFraud:* the flagged fraud online payments


## Method/Strategy:

1. Importing and Cleaning the data
2. Performing exploratory data analysis on categorical and Continuous variables including target variables. Studying their distribution for both the class of target variable to understand the type of online payments where fraudulent mostly seen and its nature.
3. Feature engineering and preparing test, train data(20-80 split). Addressing target class imbalance, if we come across it(which most probably we will). Random Under sampling, Random Over Sampling and penalise algorithms will be used here.
4. Running Logistic Regression, KNN, Random Forest Classifier, Gradient Boost and SVM supervised learning models. Comparing their performance.
5. Important features will be plotted and explored from the best performing model.

## EAD:
### What type of online payments are the victims of fraudulent payment?
![image](https://user-images.githubusercontent.com/81338075/170841963-d5b7754c-9c5f-4744-9bce-9b3640428a3a.png)
Most number of fraud payments are observed in Transfer(51%) and Cashout(49%) type of payments.

### What is the nature of a fraud online payment?
![image](https://user-images.githubusercontent.com/81338075/170841969-e423bc43-340e-46a1-bfca-a3d13d7fbde0.png)

Fraud online payments observed to have the following features;
1.  Roughly similar number of cases across all unit of time(steps),
2.  Lower amount per payment(<2Million)
3.  The range of oldbalanceDest and newbalanceDest is sparsely covered by fraud payments
4.  Both oldbalanceOrg and newbalanceOrig seem to have a higher rate of decrease for legitimate payments as compared to fraud payments.

### As fraud transactions are rare as compared to legitimate transactions so the dataset is naturally imbalanced. How to mitigate this problem?
![image](https://user-images.githubusercontent.com/81338075/170842159-b4f15564-17c8-43d0-9afc-709bf19bfcb9.png)
The dataset is highly unbalanced. 6354407 transactions are legitimate and 8213 transactions are fraudulent in the dataset, which is approx. 0.13% of the total number of transactions
This class imbalance problem is addrressed by introducing
* Random under sampling
* Random over sampling
* Panalise algorithm  approaches. 

## Models:
Here the training dataset is trained for imbalanced, Random under sampled, Random over sampled target class for all the following machine learning models

* Logistic Regression
* KNN
* Random Forest
* XGBoost
* SVM  
Panalised target class(Only for SVM)

Comparision of the performance of all 5 models is

<img width="488" alt="Screenshot 2022-05-28 at 2 49 53 PM" src="https://user-images.githubusercontent.com/81338075/170842461-9323baf4-3879-4c5d-813a-11ecb20494e8.png">

### Comparison of performance of various supervised classification models and finding which model gets maximum benefit after target classes are balanced? 
On comparing their performance interms of G-mean score, we clearely observe the; 
1.  Gradient Boost model is best benefited by it with more than 120% improvement with respect to imbalanced class performance.
2.  Random forest classifier trained with Random under sampled data is a highly efficient model to classify Fraud online payments.

### What are the important features to detect fraudulent online payment?

![image](https://user-images.githubusercontent.com/81338075/170842558-eac98f11-4843-4040-b831-0a7e5cae49f8.png)

Amount, Type, OldbalanceOrg, NewbalanceOrig are the four most important features in detecting online fraud payments.

## Practical Uses:

1.  *Reduces operational cost:* There’s no need to spend as much time and resources on reviewing every alerted transaction due to better accuracy and automated prediction.
2.  *Detects and prevents payment fraud more effectively:* Machine learning can quickly adapt to new behaviours of fraudulent transactions and helps to improve reactions to suspicious outliers.
3.  *Reduces false negatives*
4.  *Works with large datasets:* Machine learning is better than humans at processing large datasets and its prediction results improve as datasets grow.

## Limitations:

1.  The models which are trained on under sampled data see less information than in the original set of legitimate transactions. This affects the specificity of the model. 
2.  The sample chosen by random under-sampling may be a biassed sample. 
3.  The models which are trained on over sampled data may tend to overfit sometimes, since it replicates the minority class events.

## Future Research:

1.  Having Larger dataset especially more fraud events can improve the performance.
2.  Application of Artificial Neural Networks to discover more effective features(non linear combinations of original features)







