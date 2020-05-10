# Credit-Card-Fraud-Detection

Credit Card Fraud Detection is a classic class-imbalance problem where the number of fraud transactions is much lesser than the number of legitimate transaction for any bank. Most of the approaches involve building model on such imbalanced data, and thus fails to produce results on real-time new data because of overfitting on training data and a bias towards the majoritarian class of legitimate transactions. Thus, we can see this as an anomaly detection problem.

## Data

We make use of the Kaggle Credit Card Fraud Detection Dataset, which has the following information:

- The input features are V1-V28, which are unknown due to confidential reasoning.
- The Time, Amount features are reflective of general behaviour of transactions.
- The Target variable is Class which has the following labels:
  - Class 0: Legitimate Transactions
  - Class 1: Fraud Transactions
- Dataset Link: <a href="https://www.kaggle.com/mlg-ulb/creditcardfraud">Click Here</a>

## Libraries used
- Numpy
- Pandas
- Matplotlib
- Seaborn
- PyOD by CMU
- Scikit-Learn
- mlXtend

## Motivation

- Learning to handle imbalanced class datasets
- Studying the theoretical idea of Cost Sensitive Learning with Misclassification Penalty
- Determining a relationship between fraud transaction and amount of money

## Files in the repository

- Data: The Credit Card Fraud Detection Dataset File in Kaggle through a link as aforementioned
- Model.ipynb: Notebook containing the analysis of multiple classifiers on the Data
- Images: The collection of plots and output results from the code


## Analysis summary

### What is the relationship between the fraud transactions and amount?

> The fraud transactions are always for an amount less than 2500 which is to avoid suspicion from the bank security teams.

From the below Facet Grid scatter plot, we can easily see that there are no fraud transactions for any amount above 2500 and to prove our hypothesis we further analysed the data as shown in the code.

![alt-text](https://raw.githubusercontent.com/vgaurav3011/Credit-Card-Fraud-Detection/master/images/amount.png)

### What is the relationship between the fraud transactions and time?

> The fraud transactions are equitably distributed throughout time, as evident from the distribution plot below.

The fraud transactions occur at randomized time throughout the data in order to prevent any suspicion from the security teams of the banks and hide within majority of legitimate transactions.

![alt-text](https://raw.githubusercontent.com/vgaurav3011/Credit-Card-Fraud-Detection/master/images/time.png)

### How can we prevent overfitting of model towards legitimate transactions?

> Synthetic Minority Oversampling commonly abbreviated as SMOTE is used to balance the difference between minority and majority classes with dataset

It oversamples the minority class by synthetically creating new data which are either copies of old data entries or modified within a certain range to prevent variation in data and equidistributes the majority and minority classes before training the model.

Before SMOTE:

![alt-text](https://raw.githubusercontent.com/vgaurav3011/Credit-Card-Fraud-Detection/master/images/unbalanced.png)

After SMOTE:

![alt-text](https://raw.githubusercontent.com/vgaurav3011/Credit-Card-Fraud-Detection/master/images/balanced_plot.png)

Hence, we prevent overfitting of the model on imbalanced data and make it useful on predicting fraud transactions on real-time or new data with a test accuracy of 99.8% for K-Nearest Neighbors Classifier.

For a visual study, we also plotted learning curve of SGD Classifier:
![alt-text](https://raw.githubusercontent.com/vgaurav3011/Credit-Card-Fraud-Detection/master/images/SGD_Learning_Curve.png)

We made use of GridSearch on each model to obtain the best feature towards predicting the class label and also to fine tune the hyperparameters of the model constructing a pipeline for each model as shown in the code. For plot curves, we made use of Google Colaboratory due to limitation of local computation which can be accessed here: <a href="https://colab.research.google.com/drive/1Wfp_8q-Ps3GKHnDJ6dUX5G78KGIbeM67">Link</a>

## Summary

- All Fraud Transactions occur for an amount below 2500. Thus, the bank can infer clearly that the fraud committers try to commit frauds of smaller amounts to avoid suspicion.
- The fraud transactions are equitable distributed throughout time and there is no clear relationship of time with commiting of fraud.
- The number of fraud transactions are very few comparted to legitimate transactions and it has to be balanced in order for a fair comparison to prevent the model from overfitting.


## Acknowledgements
- Kaggle
- FloydHub
- AnalyticsVidhya
