#### Normalization(데이터 범위 통일하고 싶을 때)
```python
(df['data'] - df['data'].min()) / (df['data'].max() - df['data']min())
# 0 - 1 사이 값으로 normalization
```
or
```python
from sklearn import preprocessing

scaler = preprocessing.MinMaxScaler()
normalized_data = scaler.fit_transform(df[['data']])
df['data'] = normalized_data
```


#### Standardization(각 데이터가 평균에서 얼마나 떨어져 있는지)
```python
(df['data'] - df['data'].mean()) / df['data'].std()
```

#### Data Binning
```python
df['data'].describe()
# check min, max value

pd.cut(df['data'], bins=3)
# divided by 3


df_max = df['data'].max() + 1
df['group'] = pd.cut(
					 df['data'], 
					 bins=[20, 30, 40, 50, 60, df_max], 
					 right=False,
					 labels=['20s', '30s', '40s', '50s', '60s'])
# right: 오른쪽값 포함 여부 [20, 30]) ... / default: (20, 30] ... 
```

##### apply()
```python
def function1(x):
	...

df['group'] = df['data'].apply(function1)
# df['data'] is passed for the argument


def isin_interval(x, n_lower, n_upper): 
	if n_lower <= x < n_upper: 
		return 'Y' 
	else: 
		return 'N'

df['data'].apply(lambda x: isin_interval(x, 25, 30))
```