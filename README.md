<h2>Bank Churn Data Science Project</h2>
<h3>Table of Content</h3>
<ul>
<li>Case Description</li>
<li>Executive Summary</li>
<li>Dataset Description</li>
<li>Feature Engineering</li>
<li>Deep Dives</li>
<li>Decision Tree Model</li>
<li>Cluster Model</li>
<li>Recommendation</li>
<li>Tableau Dashboard</li>
</ul>
<h3>Case Description</h3>
<p>The European bank has been losing customers last year. So, it had hired me as a data analyst to find out the demographic behind the high churns. I will be conducting a descriptive analysis. However, I will go one step further. I will also develop a machine learning model to help banks predict the churns for the future and develop another cluster model to identify high value customers. </p>
<h3>Executive Summary</h3>
<p>Germany branches had the highest churn rate of 36% despite of low number of clients. Its churn rate is twice as high as France’s and Spain’s. The age group between 40 and 70 had the highest churn rate. The customers with 2 products tend to stay with the bank longer, but clients with 3 and 4 financial products are very likely to close their accounts. Female customers are more likely to close their account than their male counterpart. Germany customers tend to do well financially since they have more clients with both high salaries and high balances in terms of percentage. </p>
<h3>Dataset Description</h3>
<p>The dataset has 10000 rows and 13 features. It has no null values. The customer id is the primary key. </p>

![image](https://github.com/user-attachments/assets/10867a81-aead-45a0-980a-b017c8626294)

 
<p></p>
<h3>Feature Engineering</h3>
<ul>
<li>Regroup Age feature into Less_than_40, not_40_and_70 as agex.</li>
<li>Regroup NumOfProducts as 1_3_or_4_products and 2_products.</li>
<li>For Tenure feature, combine 0 and 10 into 0_or_10_year.</li>
</ul>
<h3>Deep Dives</h3>
1.	50% of the clients are from the bank’s France branch, 25% come from Germany branch, and the last 25% come from Spain branch. Most of customers have 1 and 2 financial products. Less than 3 percent have 3 products and less than 1 percent own 4 financial products. 70% of the clients own a credit card. In terms of age, 60% are less than 40 years old; close to 40% are between 40 and 70 years old. 1.5% of the customers are over 70 years old. For the 10000 clients, 2037 customers had closed their bank account leaving 7963 customers who continue to do business with the bank.
 
![image](https://github.com/user-attachments/assets/44a8b343-63b6-41df-9f97-0253c80433dd)


2.	For churn amount and churn rate for each categorical column, some features matter more than others. For geography, around 800 churns come from France, and 800 from France, around 400 from Spain. However, Germany has the highest churn rate of 32 %, which is twice as high as those in France and Spain, whose churn rate is 16% respectively. 
3.	For genders, 1139 churns come from female, and 898 churns come from male The churn rate for female is 25%, and the male churn rate is 16%. 
4.	Each group of number of products also vary in in terms of churns. The group with the lowest churn rate of 7.5% are clients with 2 products. Clients with 3 and 4 products are very likely to churn since each of them has rate of 83% and 100% respectively. Clients with 4 products had closed their accounts 100%. 
5.	The churns for clients who are an active member has mounted to 735 people with a low churn rate of 14% comparing to those without membership of 1302 with a churn rate of 26%. 
6.	Different age group’s churn rate also varies. For the age group less than 40 years old and above 70 years old, it has the highest number of clients and the number of churns of 597, but with a low churn rate of around 9%. Age group above 70 also had a similar churn rate of 9%. However, the churn rate for the group between 40 and 70 is as high as 37%. 
7.	For the columns such as Tenures and HasCrCard, each subgroup has a very similar churn rate.

 ![image](https://github.com/user-attachments/assets/ee21ac45-733e-42d6-83d2-433ba7947de9)


8.	For the numerical values, clients who churned tend to be older than clients who stayed since the mean age for churned clients is 44 years old, contrary to not churned customers, whose average age is 38 years old.
9.	For the balance, churned customers tend to have more money in their banks than customers who choose to stay. The average balance of churned customers is 91 thousand dollars. The average balance of the customers not churned is just 72 thousand dollars. The gap is strikingly different. For credit scores and estimated salary, two groups are very similar.
 
 ![image](https://github.com/user-attachments/assets/f3b22a96-9946-4fcc-90e2-2d46f73de559)

 ![image](https://github.com/user-attachments/assets/3435c811-da98-4b00-b1dc-6e5d3b31a3e6)



<h3>Decision Tree Model</h3>
<ul>
<li>Apply all the features for the model. Set Exited as target variable. </li>
<li>Apply LabelEncoder to turn object features into numerical features. </li>
<li>Apply GridSearchCV to find the best parameters. Parameters are max_depth and min_sample_leaf, and criterion. </li>
<li>The best parameters are {criterion:gini,max_depth:2, min_samples_leaf:15}. </li>
<li>The train accuracy score is 79.925% and the test accuracy score is 79.75%. There is no overfitting. </li>
<li>Precision and recall for the negative case or customers who are not churned is 89% and 85%.</li>
<li> Precision and recall for the positive case or customers who churned is 50% and 58%. </li>
<li>Apply Decision Tree model feature_importances feature to fetch the most important features. They are agex and NumOfProducts. </li>
<li>Reapply agex and NumOfProducts as predicting variables and Exited as target variable. </li>
<li>The best params is {max_depth:2, min_sample_leaf:5}. </li>
<li>The train and test accuracy are 79.925% and 79.75%. The precision recall for the churns are 50% and 58%. They are the same as the first model. </li>
<li>The precision and recall curve had showed the precision and recall didn’t cross. The curve means both scores come at each other’s expenses. We can have a 100% recall by lower the threshold to 0%; however, we can only have a precision as high as 50% even if we raise the threshold to 100%. </li>
<li>AUC score is 65%. It means that the model has 65% of a chance that a randomly selected positive class has a higher predicted probability than a randomly selected negative class observation.  </li>
</ul>

![image](https://github.com/user-attachments/assets/1a968d0d-b6c0-4675-9c36-e141b645386b)

![image](https://github.com/user-attachments/assets/d2d84af1-8955-47bb-8686-685cf684b921)

![image](https://github.com/user-attachments/assets/6f91509b-8e33-4326-9503-2546a8bde3eb)

 
 
<h3>Cluster Model to Identify High Value Customers</h3>
<ul>
<li>Apply PCA to downsize features. According to pca explained_variance_ratio, 2 components would be sufficient to capture all the features. </li>
<li>According to inertia of kmeans model, 4 clusters are the optimized option to cluster the dataset.</li>
<li>The New clusters can be labeled as “high_balance_high_salary”, ”high_balance_low_salary”,”low_balance_high_salary”,”low_balance_low_salary”</li>
<li>The high value customers are high balance high salary. However, it also has a high churn rate. </li>
</ul>

 ![image](https://github.com/user-attachments/assets/d233f2ac-bfa1-4f38-8ddf-378fe84a0d9b)


 ![image](https://github.com/user-attachments/assets/2e51f79b-9b22-45ad-ae34-856b56bb687d)

![image](https://github.com/user-attachments/assets/9986e015-d8c4-478f-a35a-3cea66b9303a)


 ![image](https://github.com/user-attachments/assets/5d01d163-cba8-4426-ba02-887985875644)

 

<h3>Recommendations</h3>
<ul>
<li>Focus on recruiting customers under 40 years old since they are less likely to close their accounts. </li>
<li>Try not to recommend more than 2 financial products to customers since after they have more than 2 products they would close their accounts. </li>
<li>Recruit more Germany customers since they have higher salary and higher balance. However, they also have a high churn rate, so more research should be done how to keep them longer as customers. </li>
</ul>
<h3>Tableau Dashboard</h3>
<p>Here is the <a href="https://public.tableau.com/app/profile/kun.bi/viz/bank_dashboard_17403399426080/Customer_Churn_Dashboard">link </a>of dashboard to view the churn rate across different features and help to identify high value customers filtered by countries. </p>

![dashboard](https://github.com/user-attachments/assets/bd2453d9-a733-4244-9ebb-b8ec9a91cd34)

