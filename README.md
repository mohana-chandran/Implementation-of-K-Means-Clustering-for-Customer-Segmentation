# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start
2. Data Preparation: Load and explore customer data.
3. Determine Optimal Clusters: Use the Elbow Method to find the best number of clusters.
4. Apply K Means Clustering: Perform clustering on customer data.
5. Visualize Segmented Customers: Plot clustered data to visualize customer segments.
6. End

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Yogesh. V
RegisterNumber:  212223230250
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++")
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")

km = KMeans(n_clusters=5)
km.fit(data.iloc[:, 3:])

KMeans(n_clusters=5)

y_pred = km.predict(data.iloc[:, 3:])
y_pred

data['cluster'] = y_pred
o = data[data['cluster'] == 0]
p = data[data['cluster'] == 1]
q = data[data['cluster'] == 2]
r = data[data['cluster'] == 3]
s = data[data['cluster'] == 4]

plt.scatter(o['Annual Income (k$)'], o['Spending Score (1-100)'], c="red",
         label="cluster0")
plt.scatter(p['Annual Income (k$)'], p['Spending Score (1-100)'], c="blue",
         label="cluster1")
plt.scatter(q['Annual Income (k$)'], q['Spending Score (1-100)'], c="green",
             label="cluster2")
plt.scatter(r['Annual Income (k$)'], r['Spending Score (1-100)'], c="orange",
             label="cluster3")
plt.scatter(s['Annual Income (k$)'], s['Spending Score (1-100)'], c="magenta",
             label="cluster4")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.legend()
plt.title("Customer Segments")
```
## Output:
![Screenshot 2024-10-26 193651](https://github.com/user-attachments/assets/7faeba11-8e95-4ece-aba1-026bb53601a6)
![Screenshot 2024-10-26 193703](https://github.com/user-attachments/assets/d0c78089-78fa-426e-bdbd-593003741109)

![Screenshot 2024-10-26 193713](https://github.com/user-attachments/assets/666308a3-a9e0-4ba7-bc91-0b62902853ac)
![Screenshot 2024-10-26 193735](https://github.com/user-attachments/assets/b2143754-1a7b-4163-9fb9-7bcfa699b7dc)
![Screenshot 2024-10-26 193750](https://github.com/user-attachments/assets/8956373c-a318-47d5-b346-47fb5c15158c)
![Screenshot 2024-10-26 193808](https://github.com/user-attachments/assets/a589de2d-1440-4848-9ee7-22ee7e1d1c8a)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
