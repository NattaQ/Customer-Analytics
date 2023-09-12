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

<img width="450" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/fe543284-dcf3-483e-8799-c846ac3ff265">



From Pic.1, we can see some column contian NaN and If we looking into detail we'll see some data must be clean i.e. word change from "Phone" to "Mobile Phone", "CC" to "Credit Card" and "COD" to "Cash on Delivery"

### Remove rows contained with NaN

Actualy, there have many ways to manage with NaN in DataFrame such as Fill with a number, Fill with mean, Fill with Medium or you might build model to predict value of NaN. 
But it have another way to do with NaN is remove its from our DataFrame. By this way, the good point is our Data Set will be so clean but on other side dome to our data must be remove. 

And this time we're going to remove rows contained with NaN

Pic.2

<img width="224" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/881d8805-23a1-49e7-a9ca-1485544ce2f5">

From Pic.2, our data was reduce from 5,630 to 3,774 rows. 


### Word Cleaning

On Column PreferredLoginDevice & PreferedOrderCat
- Phone to Mobile Phone

On Column PreferredPaymentMode
- CC to Credit Card
- COD to Cash on Delivery

Pic.3

<img width="304" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/ddd25480-776a-4fb6-a283-d58b34f0c345">



### One-Hot Encoding

For convert text to numerical which apply to column
- PreferredLoginDevice
- PreferredPaymentMode
- Gender
- PreferedOrderCat
- MaritalStatus

Pic.4

<img width="439" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/b2e64f97-7ea8-4482-af2a-33a1f2255ffb">




### Model Creation and Evaluation

After we finished Clean Data process, then we'll train and evaluate our mode.
From our data we have, we assume y is column Churn and the rest except CustomerID will be X (or features)

*Standardize the features*

First we did Standardize the features because different features in a dataset can have different units or scales.
Standardizing the features scales them to have zero mean and unit variance, making them comparable and preventing the model from assigning undue importance to features with larger scales.

*Process with imbalance data*

Before we go to next process let see ratio between Churn and Not Churn in the data we have 

Pic.5

![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/2f400f30-e607-4d95-a7a6-2fcacb51a9fc)


We can see impalance data number of customer between Churn and Not Churn 
\
\
*Standardize the features*

Pic.6

<img width="314" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/3cd3377e-e4a3-41c4-9e3d-492e50fa44ff">

\
\
*Separate Train & Test*

Then we separated Train & Test dataset

Pic.7

<img width="336" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/b66551b1-7527-42c1-b29d-2170ce2f3bd9">

*Process with imbalance data*

Pic.8

<img width="314" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/cf0ad8b9-c640-4a08-963d-c6498b2c3a09">

\
\
Now, our data is ready to evaluate. 

*Fit Evaluate*

Create Generic function to fit data and display results/predictions

Pic.9

<img width="337" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/4fcf9839-63dc-4c4f-9edf-e8872ac285e7">



- Apply with KNN

Pic.10

<img width="455" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/240ee25d-b11e-458b-932f-84d241570898">



![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/72846c61-e33d-4fdd-a63f-5c06ea2f947e)


![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/3c26e114-0be5-4153-9cbe-de01f7bdffe7)



- Apply with Random Forest

Pic.11

<img width="293" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/29b53ea2-bcc8-4b01-8eab-ad4322b85103">



![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/0235bbff-3872-48f9-b254-59a7e4df0d60)


![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/dd23ea1e-e8e3-4506-ad61-fdf2922cdd4e)



From Pic.10 & Pic.11, Random Forest would be save the model and use to predict Customer Churn in the future.

<img width="326" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/144fb7b0-185d-4064-afad-829d338635e3">



# Campaign Scoring
\
Campaign scoring is a technique used to identify and target customers who are at risk of churning or leaving a business. The goal is to take proactive measures to retain these customers by offering them tailored incentives or engagement strategies. 
