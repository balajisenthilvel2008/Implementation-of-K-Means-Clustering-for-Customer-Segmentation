# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages using import statement. 
2. Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head(). 
3. Import KMeans and use for loop to cluster the data. 
4. Predict the cluster and plot data graphs. 
5. Print the outputs and end the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: BALAJI S
RegisterNumber:  212225220015
*/
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
data=pd.read_csv(r"C:\Users\acer\Downloads\Mall_Customers.csv")
data.tail()
```

<img width="857" height="275" alt="image" src="https://github.com/user-attachments/assets/cbbdce2c-7f69-49b0-80b8-692b1725c2bb" />

```
data.info()
```

<img width="742" height="336" alt="image" src="https://github.com/user-attachments/assets/5fd116cc-01fb-4127-8065-ebb5f2180131" />

```
data.isnull().sum()
```

<img width="656" height="173" alt="image" src="https://github.com/user-attachments/assets/cb8ae76e-1de5-4bf3-93e9-1d19ca030410" />

```
wcss=[]
for i in range(1,11):
    kmeans=KMeans(n_clusters=i,init='k-means++')
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No of clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
```

<img width="1093" height="701" alt="image" src="https://github.com/user-attachments/assets/af544d74-e4ef-4126-8d56-676e65c20c9e" />

```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
```

<img width="923" height="290" alt="image" src="https://github.com/user-attachments/assets/88c0b879-bc37-4002-ac15-4338afe248ce" />

```
data['cluster']=y_pred
df0=data[data['cluster']==0]
df1=data[data['cluster']==1]
df2=data[data['cluster']==2]
df3=data[data['cluster']==3]
df4=data[data['cluster']==4]
plt.scatter(df0['Annual Income (k$)'],df0['Spending Score (1-100)'],c='black',label='cluster1')
plt.scatter(df1['Annual Income (k$)'],df1['Spending Score (1-100)'],c='cyan',label='cluster2')
plt.scatter(df2['Annual Income (k$)'],df2['Spending Score (1-100)'],c='yellow',label='cluster3')
plt.scatter(df3['Annual Income (k$)'],df3['Spending Score (1-100)'],c='blue',label='cluster4')
plt.scatter(df4['Annual Income (k$)'],df4['Spending Score (1-100)'],c='green',label='cluster5')
plt.legend()
plt.title("Customer Segments")
plt.show()
```

<img width="892" height="691" alt="image" src="https://github.com/user-attachments/assets/3c2d8a51-e46a-4d8c-8c3d-1414eb770d6d" />

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
