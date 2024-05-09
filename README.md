# Exno:1
Data Cleaning Process

# AIM:
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation:
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm:
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output:
```
import pandas as pd
df=pd.read_csv('/content/SAMPLEIDS.csv')
df
df.head()
df.tail()
```
![Screenshot 2024-02-23 155627](https://github.com/LINGARAJA-L/exno1/assets/129825857/50f59bc4-854d-44ed-a5a7-58e2db4ed670)

```
df.info()
```
![Screenshot 2024-02-23 155627](https://github.com/LINGARAJA-L/exno1/assets/129825857/c1652bc4-1221-43d7-9b43-caa041e9e504)

```
df.describe()
```
![Screenshot 2024-02-23 155639](https://github.com/LINGARAJA-L/exno1/assets/129825857/06daaaa1-c30f-4862-b074-d382efa80330)

```
df.shape
```
![Screenshot 2024-02-23 155639](https://github.com/LINGARAJA-L/exno1/assets/129825857/3e10b016-b53b-42cc-8760-8dc37ce380a0)

```
df.isnull().sum()
```
![Screenshot 2024-02-23 155639](https://github.com/LINGARAJA-L/exno1/assets/129825857/fdd16109-48a7-43ca-9f24-0d33c7f1dd7f)

```
x=df.dropna(how='any')
x
```
![Screenshot 2024-02-23 155648](https://github.com/LINGARAJA-L/exno1/assets/129825857/d08986ef-512d-41db-96ea-3b361d394462)

```
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
![Screenshot 2024-02-23 155655](https://github.com/LINGARAJA-L/exno1/assets/129825857/0bab79c0-b06d-4fee-be85-62ecf39d9e30)

```
df.fillna(0)
```
![Screenshot 2024-02-23 155709](https://github.com/LINGARAJA-L/exno1/assets/129825857/5dd90d31-5c22-4859-ba11-265eaa09bbb8)

```
mn=df.TOTAL.mean()
mn
```
![Screenshot 2024-02-23 155715](https://github.com/LINGARAJA-L/exno1/assets/129825857/f54a9796-7190-4ffa-9fba-ea52b144277d)

```
df.TOTAL.fillna(mn,inplace=True)
for x in df.index:
  if df.loc[x,"AVG"]>100:
    df.drop(x,inplace=True)
df
```
![Screenshot 2024-02-23 155715](https://github.com/LINGARAJA-L/exno1/assets/129825857/ebeda40e-32f2-450d-a2fb-e4c2d1103d04)

# Outlier Detection and Removal :
## Coding and Output:
```Python
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
dff=pd.DataFrame(age)
dff
```
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/28a59ebe-bdcc-4f04-93be-c29c353cdcb0)

### 15) Boxplot:
```Python
dsf=sns.boxplot(dff)
```
     
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/9876bce8-ef7f-49b2-8a97-114162113c71)


### 16) Scatterplot:
```Python
dsf=sns.scatterplot(dff)
```
   
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/8144b619-8a24-44fd-a670-d317c88e81f9)



### 17) IQR:
```Python
q1=dff.quantile(0.25)
q2=dff.quantile(0.5)
q3=dff.quantile(0.75)
iqr=q3-q1
iqr
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/5ce6b72c-20d6-4542-a6ef-f607de82fc3d)

    
### 18) Checking the high and low value:
```Python
low=q1-1.5*iqr
low
high=q3+1.5*iqr
high
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/23185839-8632-43ee-bd1c-33da6ec53f9c)

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/aef8585c-4c27-4d68-a0cb-653026339b45)


    
### 19) Filtering outlier value:
```Python
dff=dff[((dff>=low)&(dff<=high))]
dff
```
     
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/a350867b-a6c0-4d3a-94fa-7e13b6874499)

    
### 20) Dropping the null value:
```Python
dff.dropna()
```

              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/e89a47bf-418b-4d60-9c75-f4e150bde470)


    
### 21) Box plotting after filtering outlier:
```Python
sns.boxplot(data=dff)
```
     
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/b26c5fa9-3286-4299-a3e0-462659b72e6d)

  
### 22) Z Score:
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```
 
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/c81cd121-42a2-4608-892b-33755423d018)

### 23) Z Score:
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
data={'weight':[12,15,18,21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57,60,63,66,69,202,72, 75, 78, 81, 84, 232, 87, 90, 93,96,99,258]}
ds=pd.DataFrame(data)
ds
```

#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/c81cd121-42a2-4608-892b-33755423d018)

    
### 24) Z Score:
```Python
sns.boxplot(data=ds)
```

              
#### OUTPUT:
![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/a1afb418-e531-4eaa-9f0f-db5be7b0c20c)

    
 ### 25) Z Score:
```Python
z=np.abs(stats.zscore(ds))
z
```
   
#### OUTPUT:
![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/f52c84e7-00eb-4c8e-b5a7-653ea094ed1f)




### 26)Z score :
```Python
print(ds[z['weight']>3])
```


#### OUTPUT:
![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/5deaf50a-9342-48f4-ae99-1cc751d39320)

# Result:
The data clearning has beeen done successfully.
