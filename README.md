# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
step 1: Load the customer data into a Pandas DataFrame.

step 2: Select relevant features for clustering (e.g., annual income, spending score).

step 3: Standardize the features to ensure equal importance.

step 4: Use the Elbow Method to find the optimal number of clusters.

step 5: Create a K-Means clustering model with the chosen number of clusters.

step 6: Fit the model to the scaled data.

step 7: Assign cluster labels to each data point.

step 8:Analyze the characteristics of each cluster to gain insights into customer segments.
## Program:
### Program to implement the K Means Clustering for Customer Segmentation.
#### Developed by: MADHANRAJ P
#### RegisterNumber:  212223220052
```python
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No of Cluster")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

KMeans(n_clusters=5)

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```
## Output:

![image](https://github.com/user-attachments/assets/de3a9a42-3a88-4861-9b0c-06836154668a)

#### y_pred
![image](https://github.com/user-attachments/assets/a21b62fe-f81d-433c-9e7e-96bf2e06040c)

#### Cluster
![image](https://github.com/user-attachments/assets/5b0765e9-57f1-4cd4-978d-d34d4d963505)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
