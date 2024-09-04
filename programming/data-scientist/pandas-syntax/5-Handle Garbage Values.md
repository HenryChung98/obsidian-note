#### Find Missing Values
```python
df.info()
# show info(non-null count, dtype, etc)

df.isna()
# return boolean table(true if NaN else false)

df.isna().sum()
# num of NaN

df.isna().any(axis=1)
# row 방향으로 missing value 있는지 없는지 확인 / axis=0 행방향으로

df[df.isna().any(axis=1)]
# return rows which have missing value
```

#### Handling Missing Values
```python
df.dropna()
# delete rows which have missing value

mean = df['col'].mean()
df['col'].fillna(mean)
# fill NaN to mean value

df.isna().sum()
# check
```

#### Find Duplicated Values
```python
df.duplicated().sum()
# num of duplicated

df[df.duplicated()]
# 모든컬럼 값이 다 똑같을때 나옴

df[df.duplicated(subset='id', keep=False)]
# id만 중복되어도 나옴
```

#### Handle Duplicated Values
```python
df.drop_duplicates()
# delete duplicated rows

df.drop_duplicates(subset='id', keep='first')
# id가 중복될때 처음값빼고 지움

df.drop_duplicates(subset='id', keep='last')
# id가 중복될때 맨 나중값빼고 지움
```

#### Find Outlier Values
```python
1st_quantile = df['data'].quantile(0.25)
3rd_quantile = df['data'].quantile(0.75)
iqr = 3rd_quantile - 1st_quantile

lower_limit = 1st - 1.5 * iqr
upper_limit = 3rd + 1.5 * iqr

mask = (df['data'] < lower_limit) | (df['data'] > upper_limit)
df[mask]
```

#### Handle Outlier Values
```python
condition1 = df['data'] >= lower_limit
condition2 = df['data'] <= upper_limit
df[condition1 & condition2]
# 이상점 제외하는 방법
```