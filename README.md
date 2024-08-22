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
                        Data Cleaning
```
```
import pandas as pd
df=pd.read_csv('/content/SAMPLEIDS.csv')
df
```
![image](https://github.com/user-attachments/assets/ea84267f-3470-439f-9714-6c54cb660d9b)
```
df.isnull().sum()
```
 ![image](https://github.com/user-attachments/assets/09e4bf40-e343-40fa-b71f-df1f50883705)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/fdb1629f-7057-4a23-82bf-585ac5a6f92c)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/980e85e2-ed13-4adb-a8ab-279a055f2b63)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/8348acb2-3796-46b5-b026-56007d51a717)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/685e5b5a-0174-457c-8937-55d3074509ec)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/07d025e1-810f-490d-aeae-08733c214682)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/1c480f9b-723d-446f-8503-7b82c7f679a9)
```
df.fillna({'GENDER':'FEMALE','NAME':'SABEEHA','ADDRESS':'CHITTOOR','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/d89aa3da-ac0a-4dfc-8a2b-433ab0f753e8)
```
                     IQR(Inter Quartile Range)
```
```
import pandas as pd
ir = pd.read_csv('/content/iris.csv')
```
![image](https://github.com/user-attachments/assets/e82f08fc-2cb9-4a6a-97f7-9a565182c49c)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/06528a93-2620-4242-9282-84888fca94ec)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/7cc9237a-b6a7-49f7-a00a-ae5a5f79b3f4)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq = c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/026ca6b7-2c7d-4f9a-808b-3fec62584bee)
```
rid = ir[((ir.sepal_width < (c1 - 1.5 * iq)) | (ir.sepal_width > (c3 + 1.5 * iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/54a9b864-3dcb-4243-bfae-1026a83a78ff)
```
delid =ir[~((ir.sepal_width < (c1 - 1.5 * iq)) | (ir.sepal_width > (c3 + 1.5 * iq)))]
delid
```
![image](https://github.com/user-attachments/assets/13ed060b-05fb-4bcd-9459-58ee47e5365b)
```
sns.boxplot(x='sepal_width', data=delid)
```
![image](https://github.com/user-attachments/assets/153de1e6-c0ac-468d-9d73-590256fe76e6)
```
                             Z- Score
```
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset = pd.read_csv('/content/heights.csv')
dataset
```
![image](https://github.com/user-attachments/assets/7763ddaf-012e-46e3-8bd7-130ae3bb29b3)
```
df = pd.read_csv('/content/heights.csv')
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3 - q1
iqr
```
![image](https://github.com/user-attachments/assets/df0513ed-05dc-457d-9b3d-01286fcc3129)
```
low = q1 - 1.5 * iqr
low
```
![image](https://github.com/user-attachments/assets/58e94ca1-7d32-4421-9558-187d89586b63)
```
high = q3 + 1.5 * iqr
high
```
![image](https://github.com/user-attachments/assets/45b6ea20-7e4c-46ed-a76b-e1aef4ce4b78)
```
df1 = df[(df['height'] >= low) & (df['height'] <= high)]
df1
```
![image](https://github.com/user-attachments/assets/766cf95a-2cf8-4392-83b0-22606d6db63d)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/228626f3-48c6-41c2-b030-0ec0217057bb)
```
df1 = df[(z < 3)]
df1
```
![image](https://github.com/user-attachments/assets/69cae24a-0963-4b31-89b0-33f9c5cbd552)

# Result
Thus we have cleaned the data and removed the outliners by detection using IQR and Z-Score method.
