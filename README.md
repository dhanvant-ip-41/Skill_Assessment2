# Skill_Assessment2
## AIM:
To Perform Data Cleaning process and plots for Univariate and Multivariate analysis

## ALGORITHM:
1. Import the necessary libraries.
2. Use DataSet if needed or Create a DataSet.
3. Remove the outliers using IQR and remove the NULL and duplicate values.
4. We can use various plots like displot, boxenplot, boxplot, etc.
5. Now, just print the plot using plt.show

## Program:
Developed By : Dhanvant Kumar V                                                                                                            
Reg.No : 212224040070
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

df=pd.read_csv("/content/IOT-temp.csv")
df
```
<img width="565" alt="image" src="https://github.com/user-attachments/assets/29cec4ea-e2e5-4e01-a660-c4794ce76ac9" />

```python
df.isnull().sum()
```
<img width="167" alt="image" src="https://github.com/user-attachments/assets/cd57fa33-2a61-458d-9861-e5e0d189c2f7" />

```python
df.noted_date.fillna(method="ffill",inplace=True)
```
<img width="917" alt="image" src="https://github.com/user-attachments/assets/2de44ea4-24ac-4e24-8a01-0c519b5067a3" />

```python
df.rename(columns={'out/in':'status'},inplace=True)
df.status.fillna(method='ffill',inplace=True)
```
<img width="908" alt="image" src="https://github.com/user-attachments/assets/4ecaa43e-a44b-4aa3-b39a-9c2c1c56e092" />

```python
df.isnull().sum()
```
<img width="164" alt="image" src="https://github.com/user-attachments/assets/88c70248-dc01-4e2a-9933-c908722f1c69" />

```python
df.dtypes
```
<img width="194" alt="image" src="https://github.com/user-attachments/assets/3a497f5e-3822-4e9e-976f-6547be455ad9" />

```python
df.columns
```
<img width="512" alt="image" src="https://github.com/user-attachments/assets/f57c9542-7900-4dda-8b6e-190865892f1d" />

```python
tp=df.temp.median()
tp
```
<img width="318" alt="image" src="https://github.com/user-attachments/assets/73b93592-fcfc-4007-a139-b13fcad947c2" />

```python
df.temp.fillna(tp,inplace=True)
```
<img width="914" alt="image" src="https://github.com/user-attachments/assets/f09f5ddd-1547-450a-8a9e-ae96688001dd" />

```python
df.isnull().sum()
```
<img width="147" alt="image" src="https://github.com/user-attachments/assets/d73cd5f0-fdda-4c38-ac96-c1ac9d1595db" />

```python
sns.boxplot(data=df['temp'])
```
<img width="548" alt="image" src="https://github.com/user-attachments/assets/c8bb65fa-134a-4d15-a558-7aadade89fb7" />

```python
sns.boxenplot(data=df['temp'])
```
<img width="560" alt="image" src="https://github.com/user-attachments/assets/3232c6a4-fb27-44f2-98bc-34f3062be00a" />

```python
q3=np.percentile(df['temp'],75)
q1=np.percentile(df['temp'],25)
iqr=q3-q1
iqr
```
<img width="401" alt="image" src="https://github.com/user-attachments/assets/35274cc9-a817-4f5d-9afb-a51cdb6a6318" />

```python
LB=q1-1.5*iqr
HB=q3+1.5*iqr
LB
```
<img width="274" alt="image" src="https://github.com/user-attachments/assets/ee0dd7a3-b26e-400a-ad4a-b1f801ca32e1" />

```python
HB
```
<img width="311" alt="image" src="https://github.com/user-attachments/assets/70cf15c1-9efd-4682-be79-3bb089ea3683" />

```python
df=df[((df['temp']>=LB )& (df['temp']<=HB))]
df
```
<img width="572" alt="image" src="https://github.com/user-attachments/assets/6506b1ee-70c0-4ac8-80eb-78f420554673" />

```python
df.dropna(inplace=True)
```
<img width="839" alt="image" src="https://github.com/user-attachments/assets/a1d8f733-333e-4032-be85-d395b4197c42" />

```python
sns.boxplot(df['temp'])
plt.show()
```
<img width="565" alt="image" src="https://github.com/user-attachments/assets/ec5d43ed-0be4-4037-aa82-dcaad3c2e31f" />

```python
sns.boxenplot(df['temp'])
plt.show()
```
<img width="526" alt="image" src="https://github.com/user-attachments/assets/ed1644aa-b02f-402f-90a5-87d1018e02a4" />

```python
sns.countplot(data=df,x='status')
plt.show()
```
<img width="562" alt="image" src="https://github.com/user-attachments/assets/c8770199-5c69-4246-8f3c-6d5920f560af" />

```python
sns.displot(data=df,x='temp',hue='status',kde=True)
plt.show()
```
<img width="488" alt="image" src="https://github.com/user-attachments/assets/2763d2b0-97dc-4bd8-920c-715f7cbb4c5e" />

## RESULT:
Thus Data Cleaning process and plots for Univariate and Multivariate analysis has be done and executed successfully
