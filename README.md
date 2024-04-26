# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start the program
2. Import the necessary python libraries
3. Read the dataset of Mall_Customers csv file
4. From sklearn libraary select the cluster and import KMeans Clustering
5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method
6. Plot the graph x and y as Number of Clusters and wcss respectively
7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)
8. Stop the program

## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: RAJESH A
RegisterNumber: 212222100042
```
```PY
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/Mall_Customers.csv")

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
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
data["cluster"] = y_pred

df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="olive",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="orange",label="cluster4")
```

## Output:
![K Means Clustering for Customer Segmentation](sam.png)
### Data Head:

![8 1](https://github.com/Rajeshanbu/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118924713/d53efb62-e64f-402e-b27a-71810712b014)


### Checking For Null Data:

![8 2](https://github.com/Rajeshanbu/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118924713/f165ea09-7058-4f87-b5b7-f7d25b7d53ec)


### Data Information:

![8 3](https://github.com/Rajeshanbu/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118924713/5dc423e4-2503-4046-a728-50af2e70a15f)


### Elbow Method Graph:

![8 4](https://github.com/Rajeshanbu/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118924713/20e1eaf2-933e-4e96-af71-578ab98cfd28)



### K-means Cluster:

![8 5](https://github.com/Rajeshanbu/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118924713/30ece7ed-49f0-44f6-8450-aefe79e67f7b)

### Customer Segments Graph:

![8 6](https://github.com/Rajeshanbu/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118924713/054ab2e9-f1d6-4480-ae5b-740b42c7dcf6)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
