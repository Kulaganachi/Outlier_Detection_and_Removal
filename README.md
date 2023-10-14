## Ex:2 - Outlier_Detection_and_Removal
## AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following.

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## ALGORITHM:
STEP 1:
Read the given Data.

STEP 2:
Get the information about the data.

STEP 3:
Detect the Outliers using IQR method and Z score.

STEP 4:
Remove the outliers:

STEP 5:
Plot the datas using box plot.

## PROGRAM:
```
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
removing ouliers of bhp.csv file using Zscore of 3
from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)
```
```
import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)
Using IQR detect height outliers and print them( height_weight.csv)
Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)
Using IQR, detect weight outliers and print them( height_weight.csv)
Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
## OUTPUT:
bhp.csv:
df.head():

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/2c375bdb-12bd-4ed0-b0c4-21ef65c39017)

df.describe():

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/6aeeefd8-2037-4c8b-a44e-c6d82f787b0f)


df.info():

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/165492c5-8746-4aa1-9e11-940b9d4be711)


df.shape

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/9f4ad5a4-8e77-49f5-b212-59e30e500b99)



## BOXPLOT BEFORE REMOVING OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/29adcfe2-6417-40e1-b1e3-14201f4946a6)


## NEWDATA USING IQR

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/4d223981-a746-406b-b208-a223efa9218b)


## OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/aa858057-41ff-4e37-bf1d-44fb98c44cee)


newdata.shape

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/d6fcb87b-8104-4aec-b017-106a951c02af)


## BOXPLOT AFTER REMOVING OUTLIERS USING IQR

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/8cfd7960-640f-4ea5-834e-e754c7a2eabf)


# Zscore of 3

## NEWDATA USING Zscore

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/da151d5e-1391-4b79-ae44-66106fb75582)


## OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/8bf48255-2258-497d-a985-8d25da15506f)


newdata2.shape

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/20b5c36b-0c57-41e4-b4d4-09869f9a2ff2)


## BOXPLOT AFTER REMOVING OUTLIERS USING Zscore

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/b5a695e5-68a6-49ee-9dab-cf297c516cb2)


height_weight.csv

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/015b2748-21dc-48c0-9785-0d38980f48ba)


dataset.describe()

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/fe9bb723-3ca0-4278-94a3-0fe9ace53ede)


dataset.info()

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/5d1cb48d-159e-48b2-a6df-bed2c3677019)


## BOXPLOT BEFORE REMOVING OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/1b1249aa-1f75-401b-a64b-9fd4907e7a00)


## HEIGHT OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/519ea6e9-e395-446f-88ea-b2bdfc884b90)


## DATASET AFTER REMOVING HEIGHT OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/e2ed81bc-9d56-4134-ab73-d9fd9baf8506)


## BOXPLOT AFTER REMOVING HEIGHT OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/1e18f1e5-4978-4210-88e2-a62591856c18)


## WEIGHT OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/4cc4e289-e8d7-4f90-8f3a-18d7c877b5a9)


## DATASET AFTER REMOVING WEIGHT OUTLIERS

![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/2bebb2ea-367f-4da7-8658-e83169b147f3)


## BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![image](https://github.com/Kulaganachi/Outlier_Detection_and_Removal/assets/133641126/8abc2f26-d5a8-49cf-b315-a718c020a378)



## RESULT: 
     The given datasets are read and outliers are detected and are removed using IQR and z-score methods.





