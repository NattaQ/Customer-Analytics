# Voice of Customer

Voice of Customer (VoC) analytics is the process of collecting, analyzing, and extracting meaningful insights from both qualitative and quantitative feedback provided by customers. 
It is a crucial component of customer experience management and plays a significant role in understanding customer preferences, needs, and sentiments. 

Here we show you an example VoC of an restuarant.

## Dataset

The dataset is 30 reviews of customers visited the restuarant.

| Variable  | Description |
| ------------ | ----------- |
| ReviewID |  Review number |
| Review |  Customer's reviews or comment |

First, Dataset was imported 

<img width="416" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/45dc49de-dfb6-498b-a11b-b6947b7687a6">

## Pre process

Then we proceed to remove stopwords

<img width="613" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/95edd5e4-faf2-43bf-8058-f9ee2604bcfa">


Tokenize the sentenst to words

<img width="349" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/cbd60315-8f7b-4168-b7c2-f4146c52e58a">
<img width="427" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/e0592f68-7a98-4953-b033-c33c7cb21161">

## Topic Modeling

Topic modeling is a powerful technique in natural language processing (NLP) and text analysis that is used for make us for understanding Text Data
Topic modeling helps in uncovering the hidden thematic structure within contexts. It allows you to discover the main themes, topics, or subjects that exist in a large corpus of text data.


From Dataset we have, we can catagorize review into 4 groups by using pyLDAvis libary.

- 1st Group : Satify in Food Quality but waiting queue a bit long

  <img width="470" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/0d526194-739f-4e95-b4db-a316b2739a3c">


- 2nd Group : Satify in Food Quality and services 

  <img width="471" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/c5225120-c9e2-42d1-a85f-89ee2583f7c1">

  
- 3rd Group : Satify in Food Quality and reasonable price

  <img width="469" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/cec06ead-0cd4-403f-b565-fc04ae4af9fe">
  
- 4th Group : Unale to classify because It similar with 1st, 2nd and 3rd Group.

  <img width="470" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/ea07f313-0451-4eed-b5ad-772ec1a13521">





