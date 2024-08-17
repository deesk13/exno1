# Exno:1
Data Cleaning Process
# NAME: DEVA DHARSHINI. I
# REG.NO: 212223240026

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
DATA CLEANING
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/f0bf5b3a-ec11-4b7c-b2ca-682ed17de66b)


```
df.isnull().sum()
```
![Screenshot 2024-08-17 102409](https://github.com/user-attachments/assets/13f9cf98-a856-4ed0-92e2-582b4547997a)

```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/380859bb-5ebf-48e1-bb69-4d4a0b710571)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/5af27d38-a03f-4458-a3f5-adb803b19ead)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/0e68ebbd-2acb-461d-b43d-eb042a9ba148)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/43127bbc-a024-407f-8cf9-cb1dc11f5b78)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/43dc7c68-60b3-4dde-b70e-145e392f8e08)
```
df_dropped = df.dropna()
df_dropped                        
```
![image](https://github.com/user-attachments/assets/8064ab8d-6eef-48a6-97e2-f0db98cd7feb)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/8fba2b7d-5b0d-47b3-b95b-293ef6ace9dc)
 ## IQR(Inter Quartile Range) ##
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/101363fa-8374-457e-b9a6-695cfbffa3a6)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/c44c3acf-e086-4bff-bb01-f303b07049e2)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/ab0e68d6-9328-4ec9-845e-16e9401f33ad)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/f7d8206a-2b09-4fe8-8d82-daf85139977b)
```

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/7d19a9c8-0dd1-4943-ad35-fba6593126d2)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![Screenshot 2024-08-17 103327](https://github.com/user-attachments/assets/4baa87a4-96b8-420d-a1e4-86d08262e96f)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/b2147eb0-3df8-4913-a476-c7626508173d)
## Z-SCORE
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/d1b923e4-5614-4e90-8ceb-094652540107)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/95d58ff3-61d3-4367-a200-ddc7c439183d)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/6fe44df7-be5f-41ce-b6d3-dca711b0ca14)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/1e50e7d8-d0e1-4437-9329-ca523ea41a60)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/dbf6e31a-706e-4212-9c61-21104ea38710)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/36b46417-2186-4618-a46c-4eca0250e363)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/8510e08a-4637-4f50-be39-25c4c6337854)

# Result 
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
         
