# Customer-Segmentation

Currently, I'm studying about Customer Analytics, so I'll start with Feature creation then Customer Segmentation by using Python. 
We got an Dataset about Supermarket's customers that contain about Customer ID, Shopping date, Product Sales, Spending amount and etc.

## Dataset

As above, the dataset is data about Supermarket's customer.
It have 22 columns and 578,082 rows. 
Which the columns name and columns description is following the table down below. 

| Column Name  | Description | Type | Sample Values |
| ------------ | ----------- | ---- | ------------- |
| shop_week  | Identifies the week of the basket  | Char | Format is YYYYWW where the first 4 characters identify the fiscal year and the other two characters identify the specific week within the year (e.g. 200735). Being the fiscal year, the first week doesn’t start in January. (See time.csv file for start/end dates of each week) |
| shop_date  | Date when shopping has been made. Date is specified in the yyyymmdd format  | Char | 20060413, 20060412 |
| shop_weekday | Identifies the day of the week | Num | 1=Sunday, 2=Monday, …, 7=Saturday |
| shop_hour | Hour slot of the shopping | Num | 0=00:00 …23=23:00 00:59, 1=01:00 23:59 01:59 |
| Quantity | Number of items of the same product bought in this basket | Num | Integer number |
| spend | Spend associated to the items bought | Num | Number with two decimal digits |
| prod_code | Product Code | Char | PRD0900001, PRD0900003 |
| prod_code_10 | Product Hierarchy Level 10 Code | Char | CL00072, CL00144 |
| prod_code_20 | Product Hierarchy Level 20 Code | Char | DEP00021, DEP00051 |
| prod_code_30 | Product Hierarchy Level 30 Code | Char | G00007, G00015 |
| prod_code_40 | Product Hierarchy Level 40 Code | Char | D00002, D00003 |
| cust_code | Customer Code | Char | CUST0000001624, CUST0000001912 |
| cust_price_sensitivity | Customer’s Price Sensitivity | Char | LA=Less Affluent, MM=Mid Market, UM=Up Market, XX= unclas |
| cust_lifestage | Customer's Lifestage | Char | YA=Young Adults, OA=Older Adults, YF=Young Families, OF=Older Families, PE=Pensioners, OT=Other, XX=unclassified |
| basket_id | Basket ID. All items in a basket share the same basket_id value. | Num | 99410010000000020, 99410010000000344 |
| basket_size | Basket size | Char | L=Large, M=Medium, S=Small |
| basket_price_sensitivity | Basket price sensitivity | Char | LA=Less Affluent, MM=Mid Market, UM=Up Market, XX=unclassified |
| basket_type | Basket type | Char | Small Shop, Top Up, Full Shop, XX |
| basket_dominant_mission | Shopping dominant mission | Char | Fresh, Grocery, Mixed, Non Food, XX |
| store_code | Store Code | Char | STORE00001, STORE00002 |
| store_format | Format of the Store | Char | LS, MS, SS, XLS |
| store_region | Region the store belongs to | Char | E02, W01, E01, N03 |

## Coding

### Importing the Dataset

- First, we'll import dataset and see the example what we got by using df.head()

  Pic.1
  
  ![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/e611eb2e-2573-4edc-8f0b-00e91bd71ec8)

- We only select customer who is supermarket's member by identity at Customer who has Customer Code.

  Pic.2
  
  ![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/572dbaaf-ceb2-4a67-a99f-01b9034af10c)


### Features Creation

- Features will be use to do Clustering have totally 7 features, which they are
  
| Feature | Description |
| ------- | ----------- |
| Frequency | Times customer shopping |
| Total Time | First date of customer transaction minus with Last date of customer transaction. The last date we assume that last date in specificed time frame. |
| Mean time between purchase (MTBP) | Average how long between each transaction. |
| Lifetime | How long they be our customer. |
| Customer Lifetime Value (CLTV) | Total spending can expect to bring in from a customer for as long as remains a client. |
| Average Spending per Transaction | Average Spending per Transaction of a customer |
| Customer Price Sensitivity | Customer’s Price Sensitivity by convert to Numerical format. |
| Customer Lifestage | Customer's Lifestage by convert to Numerical format. |

Hear is guideline how to calculate each feature.

Pic.3

<img width="402" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/afcc188d-ec6d-4197-a53b-2235bdd6cd8e">
<img width="578" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/9b628237-9dd0-4d06-b3a3-e914ca8786da">


### Prepare feature before do Clustering

- Check Distribution of Data

Pic.4

![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/e1cca26d-40bf-41b0-a3fc-6f773ec8d9d9)


From Pic.4, we'll see mostly features aren't normal distribution and K-means is a distance-based clustering algorithm, and it is sensitive to the scale and shape of the features.
My oppinion, Data Transformation to Normal Distribution is nescessary by appling with PowerTransformer.

After that we can check distribution of the data and we will see.

Pic.5

![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/c34fbccf-a86a-4982-997e-9cb31d98dcb3)


### How many number of Cluster is the best

We'll know by appling Silhouette_score, by I looping for calculate Silhouette_score in range of number of cluster 2 to 12 clusters.
And the result shown that 9 clusters is the best at silhouette_score 0.2061.

Pic.6

![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/1491f39d-d79c-4ddd-9da8-3e82da947bf3)


### K-Medoids
After we got number of clusting that suite with our dataset. After that we'll do K-Medoids. 
Why K-Medoids applied instead of K-Means in this case?, because some features was created from One-Hot Encoding that the result will be numerical only 0 and 1.
Which K-means uses the mean (average) of the data points within each cluster as the cluster centroid but K-medoids uses actual data points from the dataset as the cluster centroids.

In this step, we'll get label on each customer code which cluster they are.

### Principle Component Analysis (PCA)
After we got clustering result and we need to see the result in scatter plot.
We have to use PCA for dismension reduction then we can plot the result.


Pic.7

![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/b0fc0283-28a1-4a5a-8248-5158ca43ce61)



### Feature Important 

We'll find which feature is significant feature for customer segmentation by using Random Forest. 
By we split train & test set by test set is 20% and the rest is train set.

The result was show below.

Pic.8

![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/941b4e6c-96c8-4891-9ae1-b1fd53376619)


From Pic.8 The important features are SPEND, Total_time, Lifetime, Frequency, CLTV, Average Spending per Transaction, Lifestate_OT and Mean time between purchase.

To view data easily we're resulting all of feature and customer group into a bar chart below. 

Pic.9

![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/c3ea3d43-041c-4260-befa-7f2ff28dd99b)



After we saw character of each customer group, we can catagorized them into 5 types.

| Group | Spedning | Frequency | Lifetime | Avg. spending per time | MTBP | No of Elder | Type |
| ----- | --------- | -------- | -------- | ---------------------- | ---- | ----------- | ---- |
| G. 1 | Less | Less | Long | Less | Long | Less | At Risk Customer |
| G. 2 | Moderate | Moderate | Moderate | Moderate | Moderate | More | Elder & Active Customer |
| G. 3 | Less | Lesst | Moderate | Moderate | Moderate | Less | Active customers |
| G. 4 | Less | Less | Long | Less | Long | Less | At Risk Customer |
| G. 5 | Moderate | Moderate | Long | More | Long | Less | Active Customer |
| G. 6 | Less | Less | Moderate | Less | Long | Less | At Risk Customer |
| G. 7 | More | More | Long | Moderate | Short | Less | Loyalty Customer |
| G. 8 | Moderate | Moderate | Less | More | Short | Less | New Potential Customer |
| G. 9 | Less | Short | More | Less | Short | Less | At Risk Customer |


Then we will apply the nescessary activities to each customer types to make the bussiness better.

**1. Loyalty Customer** : High spending, Hight frequency, Long Lifetime and short MTBP.
- Up selling for increase spending rate and Avg. spending per time.
- Provide higher service level than normally customer such as Special lines, Personal assistant and exclusive lounge.
  
**2. New Potential Customer** : New customer with moderate or high spending, high frequency and short MTBP.
- Up selling for increase spending rate and Avg. spending per time.
- Give and discount with limited time to increase frequency.

**3. Active Customer** : Spending rate might not much but have interval spending.
- Cross selling will be lead to increase spending rate for this group. Product recomendation might be apply.
- Give and discount with limited time to increase frequency.

**4. Elder & Active Customer** : Similar with Active customer but group member likely have many more elder member.
- Cross selling will be lead to increase spending rate.
- Find insight and promote product that be benefit with Elder group.

**5. At Risk Customers** : Less Spending, Frequency, MTBP.
- Analyst data why  the customer become At Risk Customers.
- Find insight product they might interest and promote to them.
- Initiate campiangs for Coming back customer.


