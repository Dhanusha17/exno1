# EX NO : 01 Data Cleaning Process
### Name : DHANUSHA K
### Reg No : 212223240034

### AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

### Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

### Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

### Coding and Output:
```
import pandas as pd
df = pd.read_csv("Loan_data.csv")
print(df.info())
print(df.describe())
```
![image](https://github.com/user-attachments/assets/bcb23439-0e56-46aa-8e30-8f80b8bcb471)

![image](https://github.com/user-attachments/assets/0bbd369e-e251-4b6b-92f7-ce8e092c7059)
```
print(df.isnull().sum())
```
![image](https://github.com/user-attachments/assets/7bb796f3-3ac4-43c0-9433-6f4b3feb2d09)
```
print(df.isnull().sum(axis=1))
```
![image](https://github.com/user-attachments/assets/036af080-8cbf-4f06-a054-f835389da567)
```
df = df.dropna()
df = df.fillna("O")
df = df.ffill()
df = df.bfill()
df.fillna(df.select_dtypes(include=['number']).mean(), inplace=True)
df = df.dropna()
print(df.head())
```
![image](https://github.com/user-attachments/assets/1b7b9289-b41d-4105-a789-41a93bcf2f30)
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from scipy import stats
age = [1, 3, 28, 27, 25, 92, 30, 39, 40, 50, 26, 24, 29, 94]
af = pd.DataFrame(age, columns=['Age'])
sns.boxplot(data=af, x='Age')
plt.show()
```
![image](https://github.com/user-attachments/assets/e94beaa5-a21b-4635-a0ab-0f45349cd582)
```
Q1 = af['Age'].quantile(0.25)
Q3 = af['Age'].quantile(0.75)
IQR = Q3 - Q1
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
outliers = af[(af['Age'] < lower_bound) | (af['Age'] > upper_bound)]
print("Outliers detected using IQR:")
print(outliers)
```
![image](https://github.com/user-attachments/assets/aceafe86-014e-4187-8dac-6e384b9c251d)
```
af_cleaned = af[(af['Age'] >= lower_bound) & (af['Age'] <= upper_bound)]
sns.boxplot(data=af_cleaned, x='Age')
plt.show()
```
![image](https://github.com/user-attachments/assets/02b7aaf2-657b-45e3-b6d0-e835d858e56e)
```
data = [1, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60, 63, 66, 69, 72, 75, 78, 81, 84, 87, 90, 93, 96, 99, 158]
df = pd.DataFrame(data, columns=['Values'])
sns.boxplot(data=df, x='Values')
plt.show()
```
![image](https://github.com/user-attachments/assets/1dee40d9-8dab-4383-ae78-4078123c7b85)
```
z_scores = stats.zscore(df)
outliers_z = df[(z_scores > 3) | (z_scores < -3)].dropna()
print(outliers_z)
```
![image](https://github.com/user-attachments/assets/eb84a035-54ac-4bcb-af12-a88717cbde59)

```
df_cleaned = df[(z_scores < 3) & (z_scores > -3)].dropna()
sns.boxplot(data=df_cleaned, x='Values')
plt.show()
```
![image](https://github.com/user-attachments/assets/181ee009-c684-4369-9bc8-6cc03489bd78)



           
### Result:
Thus the program to read the given data and perform data cleaning and save the cleaned data to a file was written and executed successfully.
