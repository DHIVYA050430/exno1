# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![alt text](image.png)

```
df.head(6)
```
![alt text](image-1.png)

```
df.tail()
```
![alt text](image-2.png)

```
df.shape
```
![alt text](image-3.png)

```
df.isnull()
```
![alt text](image-4.png)

```
df.fillna(200)
```
![alt text](image-5.png)
```
df.dropna(axis=1)
```
![alt text](image-6.png)
```
df.info()
```
![alt text](image-7.png)
```
df.isnull().sum()
```
![alt text](image-8.png)

```
df.isnull().any()
```
![alt text](image-9.png)
```
df.fillna(method = 'ffill')
```
![alt text](image-10.png)
```
df.fillna(method = 'bfill')
```
![alt text](image-11.png)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':'98','M2':'87','M3':'76','M4':'92','TOTAL':'305','AVG':'89'})
```
![alt text](image-12.png)

```
ir=pd.read_csv("/content/iris.csv")
ir
```
![alt text](image-13.png)
```
ir.describe()
```
![alt text](image-14.png)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![alt text](image-15.png)
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
![alt text](image-16.png)
```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
![alt text](image-17.png)
```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
![alt text](image-18.png)
```
sns.boxplot(x='sepal_width',data=delid)
```
![alt text](image-19.png)
```
z = np.abs(stats.zscore(ir['sepal_width']))
z
```
![alt text](image-20.png)
```
df1 = ir[z<3]
df1
```
![alt text](image-21.png)
# Result
Thus the Data Cleaning Process and Detecting and Removal of Outliers is executed successfully.   
