## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:

```
import pandas as pd
v = pd.read_csv("/content/Encoding Data.csv")
v
```
<img width="606" height="529" alt="image" src="https://github.com/user-attachments/assets/b9c7ca6a-3563-47ea-af34-d13a3a78a542" />

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
m=['Hot','Warm','Cold']
r=OrdinalEncoder(categories=[m])
r.fit_transform(v[["ord_2"]])
```
<img width="529" height="235" alt="image" src="https://github.com/user-attachments/assets/8c548d24-bdfd-49bc-b36d-4800c2b805f1" />

```
v['b01']=r.fit_transform(v[['ord_2']])
v
```
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
m=['Hot','Warm','Cold']
r=OrdinalEncoder(categories=[m])
r.fit_transform(v[["ord_2"]])
```

```
v['b01']=r.fit_transform(v[['ord_2']])
v
```

<img width="669" height="446" alt="image" src="https://github.com/user-attachments/assets/f02afaa6-9830-408d-938d-a893589bb52e" />

```
le=LabelEncoder()
d=v.copy()
d['ord_2']=le.fit_transform(d['ord_2'])
d
```
<img width="775" height="478" alt="image" src="https://github.com/user-attachments/assets/564fe02e-bcad-40d1-8e8b-4d41d6d9fd3a" />

```
from sklearn.preprocessing import OneHotEncoder
o=OneHotEncoder()
d1=v.copy()
p=pd.DataFrame(o.fit_transform(d1[["nom_0"]]))
```

```

d1=pd.concat([d1,p],axis=1)
d1
```

<img width="750" height="709" alt="image" src="https://github.com/user-attachments/assets/5ca872c0-8f3e-4390-adea-2a40e3535764" />


```
pd.get_dummies(d1,columns=["nom_0"])
```
<img width="831" height="654" alt="image" src="https://github.com/user-attachments/assets/180e3e85-ab06-42e4-b834-26c4fac4e6a6" />


```
v=pd.read_csv("data.csv")
v
```

<img width="535" height="378" alt="image" src="https://github.com/user-attachments/assets/4588bc09-eaa3-4fed-b467-7b8c43c63329" />


```

from category_encoders import BinaryEncoder
be=BinaryEncoder()
nd=be.fit_transform(v['Ord_2'])
v
```
<img width="662" height="339" alt="image" src="https://github.com/user-attachments/assets/f34f9247-bede-4125-a5af-9a8687ac4c3b" />


```
dfb=pd.concat([v,nd],axis=1)
dfb
```
<img width="856" height="347" alt="image" src="https://github.com/user-attachments/assets/09d1da3b-7962-4f8b-880c-e376f5a39dee" />


```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=v.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```
<img width="709" height="343" alt="image" src="https://github.com/user-attachments/assets/577fb98b-c483-4c52-94a5-5c2f77f81901" />


```
from scipy import stats
import numpy as np
v=pd.read_csv("Data_to_Transform.csv")
v
```
<img width="828" height="400" alt="image" src="https://github.com/user-attachments/assets/930fd339-4c92-4f79-84cf-af732657d6f8" />


```
v.skew()
```
<img width="477" height="206" alt="image" src="https://github.com/user-attachments/assets/45837bde-93d7-4e01-bca3-6c2ee00e521a" />


```
np.log(v["Highly Positive Skew"])
```
<img width="495" height="445" alt="image" src="https://github.com/user-attachments/assets/98bf65cf-8c53-4aaa-a243-7169bb6b4f86" />


```
np.reciprocal(v["Moderate Positive Skew"])
```
<img width="689" height="437" alt="image" src="https://github.com/user-attachments/assets/3b20f769-9123-453e-8382-c791167fcd69" />


```
np.sqrt(v["Highly Positive Skew"])
```
<img width="599" height="456" alt="image" src="https://github.com/user-attachments/assets/9aab67de-0f5f-4b03-ac0d-4eacc6fdedb6" />


```
np.square(v["Highly Positive Skew"])
```
<img width="573" height="445" alt="image" src="https://github.com/user-attachments/assets/9eaa9951-db46-4f02-aa22-82559f149585" />


```
v["Highly Positive Skew_boxcox"], parameters=stats.boxcox(v["Highly Positive Skew"])
v
```
<img width="804" height="410" alt="image" src="https://github.com/user-attachments/assets/7c7f4f5b-2240-4338-a6e1-7e8549a5eb9c" />

```
v.skew()
```
<img width="448" height="223" alt="image" src="https://github.com/user-attachments/assets/93e716b7-70a2-44d3-b9fc-4b824999ebf7" />


```
v["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(v["Highly Negative Skew"])
v.skew()
```
<img width="774" height="276" alt="image" src="https://github.com/user-attachments/assets/7f5679ec-6a8b-4ca0-921d-6a61e1eba902" />


```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
v["Moderate Negative Skew_1"]=qt.fit_transform(v[["Moderate Negative Skew"]])
v

```
<img width="822" height="828" alt="image" src="https://github.com/user-attachments/assets/3b00db0f-c2ac-4460-a1c2-1fc3d37a1dad" />


```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(v["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="773" height="402" alt="image" src="https://github.com/user-attachments/assets/29e8fc8b-f888-42b2-b78b-e46f838cd62b" />


```
sm.qqplot(np.reciprocal(v["Moderate Negative Skew"]),line='45')
plt.show()
```
<img width="687" height="413" alt="image" src="https://github.com/user-attachments/assets/d208d80d-d7e7-46e7-86ff-fdd041c2603a" />


```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
v["Moderate Negative Skew"]=qt.fit_transform(v[["Moderate Negative Skew"]])
sm.qqplot(v["Moderate Negative Skew"],line='45')
plt.show()
```

<img width="543" height="800" alt="image" src="https://github.com/user-attachments/assets/9a877c86-818b-43de-9773-d8351ea17144" />


```
v["Highly Negative Skew_1"]=qt.fit_transform(v[["Highly Negative Skew"]])
sm.qqplot(v["Highly Negative Skew"],line='45')
plt.show()
```
<img width="685" height="431" alt="image" src="https://github.com/user-attachments/assets/d78bb2e3-2e50-42d3-82b8-0343acd68bf3" />


```
dt=pd.read_csv("titanic_dataset.csv")
dt
```
<img width="873" height="751" alt="image" src="https://github.com/user-attachments/assets/3ccfc5db-8ef7-425e-abcf-985804ae360e" />


```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45')
plt.show()
```
<img width="527" height="403" alt="image" src="https://github.com/user-attachments/assets/ccea7f1c-1f05-4d93-ad4b-31886f83ebf3" />


```
sm.qqplot(v["Highly Negative Skew_1"], line='45')
plt.show()
```
<img width="574" height="424" alt="image" src="https://github.com/user-attachments/assets/45d1a26d-6724-451c-89a9-9fc95688f5d7" />


```



# RESULT:

Thus the given data, Feature Encoding, Transformation process and save the data to a file
was performed successfully

       
