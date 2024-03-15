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
           import pandas as pd

df=pd.read_csv("/content/SAMPLEDS.csv")
print(df)
<img width="478" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/babaf9de-4e2b-4c8d-8e54-37554da44d27">
print(df.head(3))
<img width="462" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/580f4668-447c-4b5f-9a5c-0af31cb31f0e">
print(df.tail(3))
<img width="450" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/acf93384-f09a-4e16-a376-1492f1ca992a">
x=df.dropna(how='any')
print(x)
<img width="447" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/25886349-3664-4624-bf86-f626e50ad15a">
x=df.dropna(subset=['TOTAL'],how='any')
print(x)
<img width="448" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/fab85aa3-d899-4660-8a65-45ed5897ca62">
df
<img width="588" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/85f58235-a94e-4b72-b09e-5213c57280b5">
mn=df.TOTAL.mean()
print(mn)
<img width="68" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/a4623e7d-7330-4292-9ad8-f49d551fa81b">
df.TOTAL.fillna(mn,inplace=True)
print(df)
<img width="451" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/ae4dc6ec-b924-465c-9c21-ff20bf9fe3cc">
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
print(af)
<img width="160" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/18db7ab6-7d30-41b3-9124-089f82546ccf">
sns.boxplot(data=af)
<img width="439" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/a92da183-cbe0-448f-bf4e-7cdac9e20a54">
sns.scatterplot(data=af)
<img width="475" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/29116ea0-348a-439a-958d-52fafbdfadbf">
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
<img width="108" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/5206edd7-5a4a-477c-85ac-af39ca8f2b24">
low=q1-1.5*iqr
low
<img width="113" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/bb2684f2-b2fd-41cd-9dd2-39c116eede05">
high=q3+1*iqr
high
<img width="98" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/c33208bf-bbad-48ff-b3fe-5732ec16380a">
af=af[((af>=low)&(af<=high))]
af.dropna()
<img width="111" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/e3c56e82-8d84-4884-b6ad-9ceab44ac510">
af=af[((af>=low)&(af<=high))]
af.dropna()
<img width="126" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/eef10a15-ed1a-476d-ab28-c90ed8ef23e6">
import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,39,42,45,65,78,202,17,19,92,56,1001,14,67,83]}
df=pd.DataFrame(data)
df
<img width="102" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/437fe9c7-3b00-410a-bd01-35d458e19366">
sns.boxplot(data=df)
<img width="454" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/90bf122f-0360-4efd-9880-656cad6b4d7d">
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
<img width="83" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/521fe0dd-41be-4a30-b2bf-72155bd132e1">
val=[12,15,18,21,24,27,30,33,39,42,45,65,78,202,17,19,92,56,1001,14,67,83]
<img width="194" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/35dd55f6-4187-4011-8235-ce8a73940381">
out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
  op=d_o(val)
  op
  <img width="70" alt="image" src="https://github.com/1808charitha/exno1/assets/132996838/5d69597e-83a9-4d4d-af75-0760e1c9ecc3">





















# Result
Thus To read the given data and perform data cleaning and save the cleaned data to a file done successfully.
