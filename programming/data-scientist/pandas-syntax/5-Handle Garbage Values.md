#### Find Missing Values
```python
# show info(non-null count, dtype, etc)
df.info()

# return boolean table(true if NaN else false)
df.isna()

# num of NaN
df.isna().sum()

# row 방향으로 missing value 있는지 없는지 확인 / axis=0 행방향으로
df.isna().any(axis=1)

# return rows which have missing value
df[df.isna().any(axis=1)]
```

#### Handling Missing Values
```python
# delete rows which have missing value
df.dropna()

mean = df['col'].mean()
# fill NaN to mean value
df['col'].fillna(mean)

# check
df.isna().sum()
```

#### Find Duplicated Values
```python
# num of duplicated
df.duplicated().sum()

# 모든컬럼 값이 다 똑같을때 나옴
df[df.duplicated()]

# id만 중복되어도 나옴
df[df.duplicated(subset='id', keep=False)]
```

#### Handle Duplicated Values
```python
# delete duplicated rows
df.drop_duplicates()

# id가 중복될때 처음값빼고 지움
df.drop_duplicates(subset='id', keep='first')

# id가 중복될때 맨 나중값빼고 지움
df.drop_duplicates(subset='id', keep='last')
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