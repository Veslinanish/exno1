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

```
ir=pd.read_csv("/content/iris.csv")
ir
```

## OUTPUT
<img width="826" height="601" alt="image" src="https://github.com/user-attachments/assets/8357a55b-1da3-45d5-84fe-80e6f8887c94" />

```
ir.describe()
```

## OUTPUT


<img width="798" height="435" alt="image" src="https://github.com/user-attachments/assets/0cc961b8-1eba-4888-a7f8-8dedc0ee1d00" />

``` 
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
```

## OUTPUT

<img width="1072" height="670" alt="Screenshot 2025-09-17 155538" src="https://github.com/user-attachments/assets/6f171343-3469-42e7-be5e-4213317935ee" />

```
 q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iqr=q3-q1
 print(iqr)
```

## OUTPUT
<img width="1488" height="200" alt="Screenshot 2025-09-17 155612" src="https://github.com/user-attachments/assets/7ba7b38c-bdf2-46aa-891c-63d7b09f32e1" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```

## OUTPUT
<img width="1373" height="340" alt="Screenshot 2025-09-17 155710" src="https://github.com/user-attachments/assets/6a69641f-3155-4d0a-8177-d319d13bb919" />


```
 rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
 rid
```

 ## OUTPUT
<img width="1035" height="647" alt="Screenshot 2025-09-17 160239" src="https://github.com/user-attachments/assets/ed7492ae-a940-4d37-905a-ed7dfba10dcc" />


```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```

## OUTPUT
<img width="1237" height="634" alt="Screenshot 2025-09-17 160402" src="https://github.com/user-attachments/assets/ce525af0-5192-4dc1-9f00-2a4c9695fd46" />


 ```
 import numpy as np
 import scipy.stats as stats
 z=np.abs(stats.zscore(ir.sepal_width))
 z
```

 ## OUTPUT
<img width="1473" height="714" alt="Screenshot 2025-09-17 160526" src="https://github.com/user-attachments/assets/4c864a92-0be7-4713-9928-a298d0630ecc" />



 

# Result
          Thus the programs are executed successfully
