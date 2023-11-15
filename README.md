### ODD2023-Datascience-Ex-04
### MULTIVARIATE ANALYSIS
### AIM:
To perform Multivariate EDA on the given data set.

### EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

ALGORITHM:
### STEP 1:
Import the built libraries required to perform EDA and outlier removal.

### STEP 2:
Read the given csv file

### STEP 3:
Convert the file into a dataframe and get information of the data.

### STEP 4:
Return the objects containing counts of unique values using (value_counts()).

### STEP 5:
Plot the counts in the form of Histogram or Bar Graph.

### STEP 6:
Use seaborn the bar graph comparison of data can be viewed.

### STEP 7:
Find the pairwise correlation of all columns in the dataframe.corr()

### STEP 8:
Save the final data set into the file.

### PROGRAM:
```
Developed by:DIVYA.K
Register number :212222230035
```
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt=pd.read_csv("titanic_dataset.csv")
dt
dt.info()
dt.set_index("PassengerId",inplace=True)
dt.shape
dt.nunique()
dt["Survived"].value_counts()

per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per

dt.rename(columns={'Sex':'Gender'},inplace=True)
dt
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
sns.catplot(x='Survived',hue="Gender",data=dt,kind="count")

fig,ax1=plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height=p.get_height()
  graph.text(p.get_x()+p.get_width()/2,height+20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
sns.jointplot(x="Age",y="Fare",data=dt)
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")

g=sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax=g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()-0.01,p.get_height()*1.02,'{0:.1f}'.
  format(p.get_height()),color='red',rotation='horizontal',size='small')

corr=dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
### OUTPUT:

![282286722-79902a6c-c3fc-4a5d-bd61-70317717c112](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/655cc890-e455-4e63-adb6-57a8a5241607)
![273399570-6801fb97-8256-4730-8429-2e6e430506f8](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/2861387a-5d81-4187-89d6-ff71aa56596c)


![273399633-48f3c47c-ddea-4023-a950-655d5affe5af](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/0d684955-2506-4f46-baca-da7b540c937f)
![282286742-2c34e9be-9f40-4aed-96cf-ca0fd562a18a](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/77834348-f442-4148-a10c-621a3c9b72a2)
![282286747-7146dbb3-61b7-4d14-a564-5dbac36288f9](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/d6e84be9-fcf2-4458-bc35-4a9135ebb6fa)
![273399662-f70e51b6-3514-46cc-b6f8-9dd94f32ecb9](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/8035a32d-a000-43a4-9d3a-31f262071ed7)
![273399687-2e783d46-b81f-4779-8a3b-220ed8129096](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/6acceb7c-407d-4f01-9536-f257d1c4c543)
![273400304-42bcaa18-8a24-4888-8544-19c23deb8e15](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/05f2628b-0b39-41b3-a84f-1cf3498dcc21)
![273400318-6dadaefc-688a-4e0b-a371-d7336e7bc400](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/9b8be4e7-3b03-41c4-be0d-31b271c95779)
![273400358-d12e102d-9044-48db-9ac2-3c8702e503b2](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/66904ad6-3203-4008-bf7e-7ad1dec93b46)
![273400387-f91bf614-19de-439a-9195-9167eff26df4](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/9837223c-b6a7-4103-a08d-599d7b8d3fe3)
![273400413-9cd019b8-1de5-4bb9-9987-7df2d4c473a6](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/fa379897-51ce-4cf1-826c-e25b9339222c)
![273400440-360661b9-c86c-48e0-a858-b2856be64048](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/01efd6d3-9c24-4473-8e15-d867a9e057a0)
![273400462-d10d0f18-e349-4157-a5c2-3acbf8ec1898](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/7829cf59-a7ea-4580-9271-53f3b6cfc480)
![273400484-4a5d9fb1-7c34-4502-9413-7fb085e766f6](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/3e0b63ef-829d-49a9-8233-4cd47a6e17fc)
![273400501-dbf61892-b4a3-4aba-aa32-e8cdfa02a566](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/15313cd1-e3c3-4b1b-bc82-4a30cfd149e1)
![273400524-56fda393-7204-4abe-a191-081f91fa4f4f](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/f68978bd-631a-439d-b174-55adfa7f21f9)
![273400593-8d415cfb-ffae-4d30-af6f-5806f542676c](https://github.com/divyakumars/ODD2023-Datascience-Ex-04/assets/119393621/8b42a158-b6b9-45da-a0e5-d406b9a3951e)









RESULT:
Thus we have read the given data and performed the multivariate analysis with different types of plots.
