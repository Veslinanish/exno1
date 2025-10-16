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
import numpy as np
import pandas as pd
data=pd.read_csv("/content/SAMPLEIDS.csv")
data
```

## OUTPUT 

<img width="1210" height="800" alt="Screenshot 2025-09-17 152957" src="https://github.com/user-attachments/assets/6bd15562-b4a7-497e-8de0-0447ec5f52f6" />


```
data.head(4)
```

## OUTPUT
 <img width="899" height="171" alt="Screenshot 2025-09-17 153220" src="https://github.com/user-attachments/assets/ed3ef12e-d67d-4402-b869-c7a84132c1a1" />

 
data.tail(7)

 ## OUTPUT
<img width="894" height="257" alt="Screenshot 2025-09-17 153426" src="https://github.com/user-attachments/assets/76e00a5f-4c8d-4ec0-bc7d-8a3298f0d6ca" />



data.isnull()

## OUTPUT
<img width="763" height="693" alt="Screenshot 2025-09-17 153528" src="https://github.com/user-attachments/assets/5819114e-67c3-4685-be37-39e2b14487a2" />


data.notnull()

## OUTPUT
 <img width="776" height="712" alt="Screenshot 2025-09-17 153717" src="https://github.com/user-attachments/assets/a7af838d-7e2e-49f2-b47d-852fe7ac29da" />


data.isnull().sum()

## OUTPUT
<img width="149" height="286" alt="Screenshot 2025-09-17 153934" src="https://github.com/user-attachments/assets/d463e27f-e8f8-4212-b96a-426422d382d5" />


data.isnull().any()

## OUTPUT
<img width="180" height="289" alt="Screenshot 2025-09-17 153959" src="https://github.com/user-attachments/assets/8f257f06-cf75-466b-aff7-dd6279a498a9" />


data.dropna(axis=1)

## OUTPUT
<img width="266" height="719" alt="Screenshot 2025-09-17 154026" src="https://github.com/user-attachments/assets/90b015d0-9665-4338-b591-a8f219ae0174" />


data.dropna(axis=0)

## OUTPUT
<img width="914" height="454" alt="Screenshot 2025-09-17 154206" src="https://github.com/user-attachments/assets/bd85c2c0-fbfe-4d86-a082-38bcf075c2d8" />


data.fillna(0)

## OUTPUT
<img width="904" height="721" alt="Screenshot 2025-09-17 154251" src="https://github.com/user-attachments/assets/0674cb67-397a-4372-b173-c3a493bd8f57" />


data.fillna(method="ffill")

## OUTPUT
<img width="920" height="780" alt="Screenshot 2025-09-17 154748" src="https://github.com/user-attachments/assets/c233d980-0460-4f25-a81c-52dab0bcfbc6" />


data.bfill()

## OUTPUT
<img width="903" height="716" alt="Screenshot 2025-09-17 154822" src="https://github.com/user-attachments/assets/d4253ac5-851b-409a-b4c1-07be43a56c19" />

 
data.fillna({'REGNO':0, 'NAME':'PRAVEEN'})

 ## OUTPUT
 <img width="917" height="722" alt="Screenshot 2025-09-17 154926" src="https://github.com/user-attachments/assets/41984e48-042b-4237-b242-12c2e72637fa" />


ir=pd.read_csv("/content/iris.csv")
ir

## OUTPUT

<img width="553" height="435" alt="Screenshot 2025-09-17 155843" src="https://github.com/user-attachments/assets/0c586df8-9716-435a-8a0c-5d911b5f3ccb" />

ir.describe()

## OUTPUT

<img width="488" height="307" alt="Screenshot 2025-09-17 155903" src="https://github.com/user-attachments/assets/c296f442-e583-4138-8e5e-03768e67144c" />

 
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)

## OUTPUT

<img width="670" height="571" alt="Screenshot 2025-09-17 160001" src="https://github.com/user-attachments/assets/83effa84-91e4-4c46-a1d8-0657206b8260" />

 q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iqr=q3-q1
 print(iqr)

## OUTPUT
<img width="342" height="136" alt="Screenshot 2025-09-17 160132" src="https://github.com/user-attachments/assets/06099d83-f624-4bb4-b28a-437626398d06" />

rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']

## OUTPUT
<img width="689" height="177" alt="Screenshot 2025-09-17 160201" src="https://github.com/user-attachments/assets/fea9aa28-c371-4a5c-8328-0ae0dd141c6d" />

 rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 rid

 ## OUTPUT
 <img width="718" height="499" alt="Screenshot 2025-09-17 160222" src="https://github.com/user-attachments/assets/134ac4bf-68a2-49b8-9699-abfe7c48b2a2" />

rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']

## OUTPUT
<img width="687" height="326" alt="Screenshot 2025-09-17 160306" src="https://github.com/user-attachments/assets/74d6bf03-18ba-47c2-8ff3-c598cf35700d" />

 import numpy as np
 import scipy.stats as stats
 z=np.abs(stats.zscore(ir.sepal_width))
 z

 ## OUTPUT
 <img width="502" height="372" alt="Screenshot 2025-09-17 160336" src="https://github.com/user-attachments/assets/80b9a8e7-d9f4-4eb9-88e1-297801a7604c" />


 

# Result
          Thus the programs are executed successfully
