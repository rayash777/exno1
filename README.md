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
# Data Cleaning
# READ CSV FILE
```
import pandas as pd
df=pd.read_csv('Loan_data.csv')
df
```
![image](https://github.com/user-attachments/assets/c9341214-cb65-4c33-926b-5b0c6d16895f)
# DISPLAY THE INFORMATION ABOUT CSV AND RUN THE BASIC DATA ANALYSIS FUNCTIONS
```
df.info()
```
![image](https://github.com/user-attachments/assets/d109a497-875b-459f-878c-2c1e157083f7)
```

df.describe()
```
# CHECK OUT NULL VALUES IN DATA SET USING FUNCTION
```
df.isnull()
```
![image](https://github.com/user-attachments/assets/f21777f7-394a-4861-a5f7-6b8038c5256d)

# DISPLAY THE SUM ON NULL VALUES IN EACH ROWS
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/a4c2bcfa-5988-468b-b2b8-7ba05a474a7a)
# DROP NULL VALUES
```
df_dropped=df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/61135c67-bead-4b54-8896-e27e6c4ed871)
# FILL NULL VALUES WITH CONSTANT VALUE "O"
```
df_fill_0=df.fillna(0)
df_fill_0
```
![image](https://github.com/user-attachments/assets/93421fd4-0167-43fa-aacd-3bad8b49f921)
# FILL NULL VALUES WITH ffill or bfill METHOD
```
df_ffill=df.ffill()
df_ffill
```
![image](https://github.com/user-attachments/assets/cc31287e-e080-4b39-ab36-7092849b3e1c)
```
df_bfill=df.bfill()
df_bfill
```
![image](https://github.com/user-attachments/assets/4270a125-10d5-4245-8234-9afb3f3e4498)
# CALCULATE MEAN VALUE OF A COLUMN AND FILL IT WITH NULL VALUES
```
df_new=df
df_new['LoanAmount']=df['LoanAmount'].fillna((df['LoanAmount']).mean)
df_new['Loan_Amount_Term']=df['Loan_Amount_Term'].fillna((df['Loan_Amount_Term']).mean)
df_new
```
![image](https://github.com/user-attachments/assets/4fd641a1-c52f-4199-8678-988b1468e37c)
# DROP NULL VALUES
```
df_new.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/3a8368f5-bf79-411d-a2c7-857f4ce055ec)

# Outlier Detection and Removal
```
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/user-attachments/assets/365ad0f4-ad31-4c86-803b-55f96154154b)
# USE BOXPLOT FUNCTION HERE TO DETECT OUTLIER
```
sns.boxplot(data=af)

```
![image](https://github.com/user-attachments/assets/c6dee0d5-2aa1-4be6-abc0-13ec038dae6d)

# PERFORM IQR METHOD AND DETECT OUTLIER VALUES
```
import numpy as np
Q1=np.percentile(age,25)
Q2=np.percentile(age,50)
Q3=np.percentile(age,75)
```
```
ivr=Q3-Q1
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
outliers=af[(af<lower_bound) | (af>upper_bound) ]
```
```
print("Quantile 1",Q1)
print("Quantile 2",Q2)
print("Quantile 3",Q3)
print("Inter Quartile Range",IQR)
print("Lower Bound",lower_bound)
print("Upper Bound",upper_bound)
print("Outliers",outliers)
```
![image](https://github.com/user-attachments/assets/93120db0-ca05-416b-a388-fabd22e1c298)
# REMOVE OUTLIERS
```
af=af[(af>=lower_bound) & (af<=upper_bound)]
af.dropna()
print("After removing outliers")
af
```
![image](https://github.com/user-attachments/assets/28b57dbc-0dc9-4243-8234-c19dec6d5f54)
# USE BOXPLOT FUNCTION HERE TO CHECK OUTLIER IS REMOVED
```
sns.boxplot(data=af)
```
# USE BOXPLOT FUNCTION HERE TO DETECT OUTLIER
```
from scipy import stats
data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,158]
df=pd.DataFrame(data)
sns.boxplot(data=df)
```

![image](https://github.com/user-attachments/assets/bace521d-34c6-4ac8-ac07-25e82a0bb97d)
# PERFORM Z SCORE METHOD AND DETECT OUTLIER VALUES
```
z=np.abs(stats.zscore(data))
print("Outlier values:")
outliers=df[z>3]
outliers
```

![image](https://github.com/user-attachments/assets/557c5ad9-b194-456f-9765-38faf9e706c5)
# REMOVE OUTLIERS
```
cleaned_df=df[z<3]
print("After removing outliers")
cleaned_df
```

![image](https://github.com/user-attachments/assets/8a1d9612-bf61-4da2-8249-ec78e2c0b28e)
# USE BOXPLOT FUNCTION HERE TO CHECK OUTLIER IS REMOVED
```
sns.boxplot(data=cleaned_df)
```

1![image](https://github.com/user-attachments/assets/4774a180-1e0a-4940-a3e1-6bf1275a5ca2)



        <<include your coding and its corressponding output screen shots here>>
# Result
          <<include your Result here>>
