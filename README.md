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
<img width="1448" height="313" alt="Screenshot 2025-09-17 153049" src="https://github.com/user-attachments/assets/025e191d-7a25-45b2-94fd-b669ed86f132" />

```
data.tail(7)
```

 ## OUTPUT

<img width="1479" height="403" alt="Screenshot 2025-09-17 153109" src="https://github.com/user-attachments/assets/ece2a319-9338-47c1-8c44-cf110505e572" />

```
data.isnull()
```

## OUTPUT

<img width="1311" height="640" alt="Screenshot 2025-09-17 153614" src="https://github.com/user-attachments/assets/3682c2ee-f199-4ef5-a93e-cd4d42e4a6ed" />

```
data.isnull().sum()
```

## OUTPUT

<img width="1311" height="640" alt="Screenshot 2025-09-17 153614" src="https://github.com/user-attachments/assets/51c453f3-02c1-4c5e-8165-f3fc4b8e24d7" />


```
data.isnull().any()
```

## OUTPUT

<img width="1455" height="637" alt="Screenshot 2025-09-17 153642" src="https://github.com/user-attachments/assets/3f70c91f-40e4-4e29-a750-bb061d2e8743" />

```

data.dropna(axis=1)
```

## OUTPUT

<img width="580" height="456" alt="Screenshot 2025-09-17 153721" src="https://github.com/user-attachments/assets/ea0035cf-bbcc-4210-aeab-58101167f6d2" />

```
data.dropna(axis=0)
```

## OUTPUT


<img width="1418" height="620" alt="Screenshot 2025-09-17 154042" src="https://github.com/user-attachments/assets/47adb8aa-a6f5-4db1-9175-21fcbab736c4" />

```
data.fillna(0)
```

## OUTPUT

<img width="1311" height="695" alt="Screenshot 2025-09-17 154430" src="https://github.com/user-attachments/assets/188733b8-3905-4f8a-962a-27737d07be3c" />


```
data.fillna(method="ffill")
```

## OUTPUT


<img width="1445" height="702" alt="Screenshot 2025-09-17 154615" src="https://github.com/user-attachments/assets/21cc2545-1c0b-402a-9c7f-fd465845a5ce" />

```
data.fillna({'REGNO':0, 'NAME':'PRAVEEN'})
```

 ## OUTPUT
 
<img width="1168" height="802" alt="image" src="https://github.com/user-attachments/assets/8d5ba248-478d-4881-9aa3-1fb48dbfc874" />




ir=pd.read_csv("/content/iris.csv")
ir

## OUTPUT



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

 ```
 import numpy as np
 import scipy.stats as stats
 z=np.abs(stats.zscore(ir.sepal_width))
 z
```

 ## OUTPUT
 <img width="502" height="372" alt="Screenshot 2025-09-17 160336" src="https://github.com/user-attachments/assets/80b9a8e7-d9f4-4eb9-88e1-297801a7604c" />


 

# Result
          Thus the programs are executed successfully
