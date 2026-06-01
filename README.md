#EX.NO:1
NAME:A.BENEDICT FERNANDO
REG NO:212225230030
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
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
<img width="1914" height="1137" alt="image" src="https://github.com/user-attachments/assets/401bc12e-32ee-4a9d-9412-9df3a23650e7" />
df.head()
<img width="1919" height="1141" alt="image" src="https://github.com/user-attachments/assets/d5a4fe80-660b-44b7-b08c-086e3795acf5" />
df.tail()
df.info()
<img width="1904" height="1133" alt="image" src="https://github.com/user-attachments/assets/434c15a2-2e74-4442-92d9-39b3df4038e2" />
df.isnull().sum()
<img width="1918" height="1141" alt="image" src="https://github.com/user-attachments/assets/7dcc1db0-114a-4ac6-a118-290ff6bdf8b0" />
df.isnull().any() 
<img width="1918" height="1144" alt="image" src="https://github.com/user-attachments/assets/fd1abe21-6123-49bc-a510-aba544bd7e3f" />
df.dropna()
df.fillna(0)
<img width="1915" height="1110" alt="image" src="https://github.com/user-attachments/assets/4466cf3b-ece5-4b23-8ce9-df0a105c59ed" />
df.fillna(method='ffill')
<img width="1908" height="1127" alt="image" src="https://github.com/user-attachments/assets/8b239541-1a71-46f3-8c5b-7722ada2c2eb" />
df.fillna({'GENDER':'MALE','NAME':'SRI'})
<img width="1837" height="1068" alt="image" src="https://github.com/user-attachments/assets/21240837-d085-4ebb-b371-a75ebe7a8cd5" />
ir=pd.read_csv("/content/iris.csv") ir
<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/97d93e41-9186-4e19-81b8-c7d8fe8f64ed" />
ir.describe()
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/20288747-5b77-4a4d-a0db-433aaf24f73c" />
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/be5a8b46-2beb-4a3e-9a13-f0384a3355c5" />
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
(IQR)=Q3-Q1
print(IQR)
<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/5c9c96cc-746e-4830-90f3-0c73ebf0f57e" />
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/de6279dc-d67a-42b6-85bc-6bea6b26b0c0" />
sns.boxplot(x='sepal_width',data=ran)
<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/cb628910-ca91-42b4-81b9-9221f3fd8195" />
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['petal_length']))
z
<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/d8e37320-ca98-4254-b27f-c37abaedf4f2" />
ir1=ir[z<3]
ir1
<img width="1600" height="950" alt="image" src="https://github.com/user-attachments/assets/2d885945-973d-4a64-b52e-8b6926b00056" />

# Result
 Thus the given data successfully performed data cleaning and saved the cleaned data to a file
