### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 18/09/2025
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```
import pandas as pd
df = pd.read_csv("clustervisitor.csv")
print(df)
cluster = {
    "young": (df['Age'] <= 30),
    "Middle": ((df['Age'] > 30) & (df['Age'] <= 50)),
    "Older": (df['Age'] > 50)
}
print(cluster)
count = []
for g,c in cluster.items():
    visitor=df[c]
    count.append(len(visitor))
    print(f'Visitors in {g} group')
    print(visitor)
    print(count)
import  matplotlib.pyplot as plt
plt.bar(cluster.keys(),count,data=df)
plt.xlabel("Age Groups")
plt.ylabel("Number of Visitors")
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:

<img width="574" height="742" alt="image" src="https://github.com/user-attachments/assets/55bf2980-3590-491f-ac05-d39d819ffa91" />

<img width="658" height="580" alt="image" src="https://github.com/user-attachments/assets/6b3b728e-be5d-4ed6-8d09-d727b2e11032" />

### Visualization:
```python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
sc=StandardScaler()
df1=df['Age']
df2=df['Income(K)']
df3=pd.concat([df1,df2],axis=1)
newdf=sc.fit_transform(df3)
newdf
kmean = KMeans(n_clusters=4,random_state=42)
df3['cluster']=kmean.fit_predict(newdf)
print(df3)
plt.scatter(df3['Age'],df3['Income(K)'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Salary in thousands')
plt.title('Kmeans Cluster')
plt.show()
```
### Output

<img width="681" height="610" alt="image" src="https://github.com/user-attachments/assets/6fc22b3f-19f0-439a-841e-cb2577c42ecc" />

<img width="1213" height="449" alt="image" src="https://github.com/user-attachments/assets/660e3590-19fb-4c2d-80a1-0c051e8e9ecc" />

### Result:
Thus, We had completed the Implementation of Cluster and Visitor Segmentation for Navigation patterns is sucessfully done by using Python programming
