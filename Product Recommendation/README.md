# Product Recommendation

This topic we're takling about Product Recommendation.

Traditional recommendation systems have employed Content-Based Filtering (CBF) and Collaborative Filtering (CF). 
CBF recommends items to a user based on the features or attributes of the items with which they have previously interacted. 
It matches the user's profile with item characteristics to provide recommendations. On the other hand, CF suggests items to a user based on the preferences and behaviors of other users who share similar tastes. 
It identifies patterns by analyzing interactions between users and items, such as ratings, likes, or purchase history.

But this time we will use CBF Technique to do Product Recommendation. 

## Dataset

We have dataset for online shopping with varies product on their website. 
And We also have historical purchasing data of each customer. 
Which sample of data is per Pic.1

Pic.1

<img width="781" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/f983ec98-0e11-47b4-8245-5d338533ebbe">

THen we drop column that doen't product out from the DataFrame and groupby customer to see quantity of each product was purchased by each customer.

Pic.2 

<img width="563" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/ecba5e03-b165-4620-bd78-2eb0312aee33">

After that, we find similarly between 211 items

Pic.5

<img width="297" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/66ec856e-efe4-4418-808b-9134abb71e3a">

Pic.6

![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/c027d58e-a2f5-4c15-a59a-fcedb939638f)

From Pic.6, the majority of items have lowersimilarity values (closer to 0), whilefewer items have higher similarityvalues (closer to 1).
This suggests that the items in datasettend to have relatively low similarity.

Next, We'll find score of pairs of distinct items with similarity scores greater than or equal to 0.65, and it presents these pairs in descending order of similarity score.

Pic.7

<img width="403" alt="image" src="https://github.com/NattaQ/Customer-Analytics/assets/115794048/298fd2a5-470b-4b00-94e5-3bd01feeb395">

Then, we created a graph representation of item similarities, where nodes represent items, edges represent the similarity between items, and the thickness of edges reflects the strength of similarity.

Pic.8
![image](https://github.com/NattaQ/Customer-Analytics/assets/115794048/d52ba767-05db-4e6c-8cac-65ac81e1fddf)

From Pic.8 , The image on the left displays a group of products that exhibithigh similarity. Only 183 pairshave co-sin similarity morethan 0.65.
Marketer leverage thisinformation to increasecustomer average spend,particularly among a customergroup who currently have thelowest average spending. Thiscan be achieved by
- Bundling : create productbundles that include highlysimilar items. Offerdiscounts for purchasingthese bundles to incentivizecustomers and encouragelager transactions.

