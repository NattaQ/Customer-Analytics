# Churn Prediction
Now, we're going to train a model to predict Churn of customer by we have example of E Commerce daset. 
By we'll compare between K-NN and Random Forest which one will give more accuracy. 


## Dataset

The dataset is data about E Commerce.

It have 20 columns and 5,630 rows.
Which the columns name and columns description is following the table down below. 

| Variable  | Description |
| ------------ | ----------- |
| CustomerID |  Unique customer ID |
| Churn |  Churn Flag |
| Tenure |  Tenure of customer in organization |
| PreferredLoginDevice |  Preferred login device of customer |
| CityTier |  City tier |
| WarehouseToHome |  Distance in between warehouse to home of customer |
| PreferredPaymentMode |  Preferred payment method of customer |
| Gender |  Gender of customer |
| HourSpendOnApp |  Number of hours spend on mobile application or website |
| NumberOfDeviceRegistered |  Total number of deceives is registered on particular customer |
| PreferedOrderCat |  Preferred order category of customer in last month |
| SatisfactionScore |  Satisfactory score of customer on service |
| MaritalStatus |  Marital status of customer |
| NumberOfAddress |  Total number of added added on particular customer |
| Complain |  Any complaint has been raised in last month |
| OrderAmountHikeFromlastYear |  Percentage increases in order from last year |
| CouponUsed |  Total number of coupon has been used in last month |
| OrderCount |  Total number of orders has been places in last month |
| DaySinceLastOrder |  Day Since last order by customer |
| CashbackAmount |  Average cashback in last month |


## Coding

### Importing the Dataset

- First, we'll import dataset and see the example what we got by using df.info()

Pic.1

<img width="758" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/3ed12bcb-cf60-47e3-95a8-0ea42233ee27">


From Pic.1, we can see some column contian NaN and If we looking into detail we'll see some data must be clean i.e. word change from "Phone" to "Mobile Phone", "CC" to "Credit Card" and "COD" to "Cash on Delivery"

### Remove rows contained with NaN

Actualy, there have many ways to manage with NaN in DataFrame such as Fill with a number, Fill with mean, Fill with Medium or you might build model to predict value of NaN. 
But it have another way to do with NaN is remove its from our DataFrame. By this way, the good point is our Data Set will be so clean but on other side dome to our data must be remove. 

And this time we're going to remove rows contained with NaN

Pic.2

<img width="594" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/434de8a5-a339-4492-89c6-4737ecdf786d">

From Pic.2, our data was reduce from 5,630 to 3,774 rows. 


### Word Cleaning

On Column PreferredLoginDevice & PreferedOrderCat
- Phone to Mobile Phone

On Column PreferredPaymentMode
- CC to Credit Card
- COD to Cash on Delivery

Pic.3

<img width="532" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/52576e43-b4cb-407b-b457-0de16f9698d9">


### One-Hot Encoding

For convert text to numerical which apply to column
- PreferredLoginDevice
- PreferredPaymentMode
- Gender
- PreferedOrderCat
- MaritalStatus

Pic.4

<img width="662" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/227ee11b-2805-44f0-bcd3-229221f67b79">



### Model Creation and Evaluation

After we finished Clean Data process, then we'll train and evaluate our mode.
From our data we have, we assume y is column Churn and the rest except CustomerID will be X (or features)

*Standardize the features*

First we did Standardize the features because different features in a dataset can have different units or scales.
Standardizing the features scales them to have zero mean and unit variance, making them comparable and preventing the model from assigning undue importance to features with larger scales.

*Process with imbalance data*

Before we go to next process let see ratio between Churn and Not Churn in the data we have 

Pic.5

<img width="661" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/d4f833f1-2f88-4f0f-87cc-cb5d92ee176f">

We can see impalance data number of customer between Churn and Not Churn 
\
\
Pic.6

<img width="463" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/5a107e4f-438f-4613-a153-325ebd3e9d36">

\
\
*Separate Train & Test*

Then we separated Train & Test dataset

Pic.7

<img width="581" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/f52e04a5-ea8b-4343-8553-52220d1672e4">

\
\
Now, our data is ready to evaluate. 

*Fit Evaluate*

Create Generic function to fit data and display results/predictions

Pic.8

<img width="710" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/6fdd6ade-73e9-48cf-85c5-fef2047edce7">


- Apply with KNN

Pic.9

<img width="698" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/01bd9aff-1a78-43d0-8356-75f82eea236d">


![image](https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/3bd44a41-b1c7-405f-bdd6-107e4f2a8f41)

![image](https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/76432d71-7cdc-46cf-951c-ba058daa6ec4)


- Apply with Random Forest

Pic.10

<img width="652" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/aadfe1b7-58a5-4240-afed-dface34d818e">


![image](https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/b0a1fe97-19d9-41cf-af72-f925a8d72ea7)

![image](https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/21891b3a-21e2-41b5-9bdb-823925041035)


From Pic.9 & Pic.10, Random Forest would be save the model and use to predict Customer Churn in the future.

<img width="557" alt="image" src="https://github.com/NattaQ/Churn-Prediction-Campaign-Scoring/assets/115794048/9a9f12a6-0d3b-4354-bb75-436651012e7e">


# Campaign Scoring
\
Campaign scoring is a technique used to identify and target customers who are at risk of churning or leaving a business. The goal is to take proactive measures to retain these customers by offering them tailored incentives or engagement strategies. 
