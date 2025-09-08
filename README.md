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
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="1288" height="697" alt="image" src="https://github.com/user-attachments/assets/8dcd6910-1852-4578-bd12-c105d341fc40" />

```
df.head()
```
<img width="1121" height="254" alt="image" src="https://github.com/user-attachments/assets/18ece433-9129-4ea3-a36c-022f5125cb4f" />

```
df.tail()
```
<img width="1173" height="247" alt="image" src="https://github.com/user-attachments/assets/eefafc4f-7bad-4147-8ce0-6151c0772ab1" />

```
df.isnull()
```
<img width="933" height="691" alt="image" src="https://github.com/user-attachments/assets/99495f3e-86a2-49b0-8d61-7781c56625b0" />

```
df.isnull().sum()
```
<img width="413" height="563" alt="image" src="https://github.com/user-attachments/assets/0528d2ab-259f-47ca-a20e-41f06e8d5025" />

```
df.isnull().any()
```
<img width="407" height="579" alt="image" src="https://github.com/user-attachments/assets/6199d9e3-34ab-422a-bca9-83b85ac8ab3f" />

```
df.dropna(axis=0)
```
<img width="1228" height="561" alt="image" src="https://github.com/user-attachments/assets/f77cf08b-3361-4b10-95ed-546c5f692c19" />

```
df.dropna(axis=1)
```
<img width="419" height="686" alt="image" src="https://github.com/user-attachments/assets/f79b142a-b325-4d9a-a410-633b54f489d4" />

```
df.fillna(1)
```
<img width="1218" height="640" alt="image" src="https://github.com/user-attachments/assets/f2a4f10a-9667-4767-a031-433d98176821" />

```
df.fillna(method ='ffill')
```
<img width="1191" height="704" alt="image" src="https://github.com/user-attachments/assets/1840e68e-ca2d-4ac9-8a27-ea40298c9908" />

```
df.fillna(method='bfill')
```
<img width="1186" height="696" alt="image" src="https://github.com/user-attachments/assets/25e5fe05-77c0-4e58-a54e-2f8d16964a4f" />

```
df.fillna({'GENDER':'MALE','NAME':'SRI','M1':'63','M2':'69'})
```
<img width="1175" height="695" alt="image" src="https://github.com/user-attachments/assets/c3f3b402-0700-48bc-bdff-d07708fdc1b6" />

```
ir=pd.read_csv('iris.csv')
ir
```
<img width="850" height="524" alt="image" src="https://github.com/user-attachments/assets/aa45fc1f-75f1-4828-bc54-795cbff2c4f8" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="837" height="587" alt="image" src="https://github.com/user-attachments/assets/5ce53fb4-dcc4-4b0e-b8fb-bce17b7b6882" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
IQR=Q3-Q1
print(IQR)
```
<img width="871" height="52" alt="image" src="https://github.com/user-attachments/assets/d9e929dd-ef34-4f9f-bc0e-b94bed2255cc" />

```
rid=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid['sepal_width']
```
<img width="336" height="262" alt="image" src="https://github.com/user-attachments/assets/5dfcf40f-74de-4a71-bd61-6392f9b32aa2" />

```
rid=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
rid
```
<img width="913" height="514" alt="image" src="https://github.com/user-attachments/assets/78091594-881b-48b2-9bf3-a38c0464c571" />

```
sns.boxplot(x='sepal_width',data=rid)
```
<img width="895" height="571" alt="image" src="https://github.com/user-attachments/assets/62df305c-7656-444f-a5d5-4c8b7f9c7ec1" />

```
import numpy as np
import scipy.stats as stats
df=pd.read_csv('heights.csv')
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
<img width="846" height="705" alt="image" src="https://github.com/user-attachments/assets/cafc35fc-c8be-42b3-b566-82777103d1c0" />

```
ir1=ir[z<3]
ir1
```

<img width="846" height="517" alt="image" src="https://github.com/user-attachments/assets/fe4ed9a4-1048-43f8-bca9-6f2388a520d1" />



           
# Result
The given data has been successfully read, cleaned by handling duplicates and missing values, and saved to a new file named cleaned_data.csv.

