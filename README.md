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
• Square Root Transforma
tion
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
print(df)
```
<img width="318" height="254" alt="image" src="https://github.com/user-attachments/assets/1707cd9e-c6a3-4b54-9583-a92c23c319b1" />

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
<img width="240" height="223" alt="image" src="https://github.com/user-attachments/assets/12d5ddc1-bcc4-472e-b19a-0cebaedc2b2f" />

```
df['bo2']=e1.fit_transform(df[["ord_2"]])
print(df)
```
<img width="362" height="247" alt="image" src="https://github.com/user-attachments/assets/a91c26c4-6ce9-4bcc-ae89-fcd0503589e7" />

```
le=LabelEncoder()
df['ord_2']=le.fit_transform(df['ord_2'])
print(df)
```
<img width="364" height="243" alt="image" src="https://github.com/user-attachments/assets/b14f5968-b61a-4394-b13a-c761ae65b17a" />

```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]])) # Orders in Alphabetical Order Blue , Green, Red
df2=pd.concat([df2,enc],axis=1)
print(df2)
```
<img width="499" height="236" alt="image" src="https://github.com/user-attachments/assets/d6e98d22-9645-4abf-9fb1-29fa04ed6f45" />

```
pd.get_dummies(df2,columns=["nom_0"])
```
<img width="701" height="369" alt="image" src="https://github.com/user-attachments/assets/5f2eb839-80e4-4ba7-9b87-682bb9ca0499" />

```
!pip install category-encoders
```
<img width="1234" height="476" alt="image" src="https://github.com/user-attachments/assets/a58ab2a6-3d4d-49e7-aefd-f6bc8db7efd7" />

```
from category_encoders import BinaryEncoder
df = pd.read_csv("data.csv")
print(df)
```
<img width="585" height="237" alt="image" src="https://github.com/user-attachments/assets/fd68cc8d-887b-4c5a-80ec-7702ab872bbf" />

```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
print(dfb)
```
<img width="781" height="494" alt="image" src="https://github.com/user-attachments/assets/d65f97f5-3a39-4e6a-8c89-5aa762204279" />

```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
print(CC)
```
<img width="680" height="242" alt="image" src="https://github.com/user-attachments/assets/63a21bde-03e4-4b16-afee-34c0f1c5e22e" />

```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("Data_to_Transform.csv")
print(df)
```
<img width="750" height="580" alt="image" src="https://github.com/user-attachments/assets/07ce960a-3e43-4179-ba5d-07c68b40e14c" />

```
df.skew()
```
<img width="351" height="112" alt="image" src="https://github.com/user-attachments/assets/579190fa-fe9f-4c1d-ac9c-032daf0a1a35" />

```
np.log(df["Highly Positive Skew"])
```
<img width="563" height="262" alt="image" src="https://github.com/user-attachments/assets/565f12e6-9410-4673-9d89-0371bed74692" />

```
np.reciprocal(df["Moderate Positive Skew"])
```
<img width="582" height="258" alt="image" src="https://github.com/user-attachments/assets/f542b04c-d559-4ab4-8ef9-3dcfd7bdd3d9" />

```
np.sqrt(df["Highly Positive Skew"])
```
<img width="564" height="264" alt="image" src="https://github.com/user-attachments/assets/287f95eb-0d1c-431c-99fb-51de7589d256" />

```
np.square(df["Highly Positive Skew"])
```
<img width="563" height="261" alt="image" src="https://github.com/user-attachments/assets/c4ce0e95-7b1d-4e90-b1d0-f70079d136dd" />

```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
print(df)
```
<img width="760" height="579" alt="image" src="https://github.com/user-attachments/assets/9b297d52-ed1d-42a4-bb1e-87e374febfcf" />

```
df.skew()
```
<img width="394" height="131" alt="image" src="https://github.com/user-attachments/assets/eb97dabd-f5ab-4792-8c98-5d7f50430976" />

```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()
```
<img width="432" height="155" alt="image" src="https://github.com/user-attachments/assets/732ee56e-364f-4a8f-b3b5-a9813d2241dc" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
print(df)
```
<img width="764" height="816" alt="image" src="https://github.com/user-attachments/assets/64e6eb23-b299-47b9-8622-1b82aa7ad948" />

```
import statsmodels.api as sm # STATS MODEL- STATISTICAL MODEL TO VISUALIZE DISTRIBUTION
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45') # QQ - QUANTILE QUANTILE PLOT
plt.show()
```
<img width="752" height="541" alt="image" src="https://github.com/user-attachments/assets/77aa66b8-f084-4f8e-9bac-08b2158b4733" />

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45') # RECIPROCAL
plt.show()
```
<img width="743" height="533" alt="image" src="https://github.com/user-attachments/assets/999d9bd2-a37c-468d-ab46-0e7e83393385" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="717" height="537" alt="image" src="https://github.com/user-attachments/assets/a8d44da9-620c-4e89-87f4-aee1d7f60817" />


# RESULT:
      Thus the Feature Encoding and Transformation process has been done for the given data.
       
