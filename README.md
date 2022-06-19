# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Start the program
2. import pandas as pd and matplotlib.pyplot as plt
3. read required csv file and print data.head(),info(),isnull().sum()
4. import kmeans and declare wcss = []
5. create for loop for KMeans and wcss.append(kmeans.inertia)
6. plot a graph for elbow method , x_label as no.of clusters and y_label as wcss
7. print km.fit(data.iloc[:,3:]) and print y_pred
8. plot the second graph for Customer Segments
9. Stop the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: S Saichandran 
RegisterNumber:  212220040138
*/
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("/content/Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
  kmeans= KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No.of clusters")
plt.ylabel("wcss") #wcss is the sum of squared distance between each point and the centroid in the clusters
plt.title("Elbow Method")
km = KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
![K Means Clustering for Customer Segmentation](/1.Data.head().PNG)
![K Means Clustering for Customer Segmentation](/2.Data.info().PNG)
![K Means Clustering for Customer Segmentation](/3.data.isnull().sum().PNG)
![K Means Clustering for Customer Segmentation](/4.Output(1).PNG)
![K Means Clustering for Customer Segmentation](/5.KMeans.PNG)
![K Means Clustering for Customer Segmentation](/6.y_pred.PNG)
![K Means Clustering for Customer Segmentation](/7.Output(2).PNG)
## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
