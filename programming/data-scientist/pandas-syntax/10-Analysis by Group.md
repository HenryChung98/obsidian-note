```python
df.groupby('column_data')
# list, dictionary, dataframe 으로 만들어짐

df.groupby('column_data').count()
# table로 나옴
df.groupby('column_data').size()
# series로 나옴

df.groupby('column_data').min()
# string도 나옴
df.groupby('column_data').min(numeric_only=True)
# 숫자만 나옴
# max, mean, sum ...

df.groupby('column_data')['data'].mean()
# data 하나만 계산해 나옴
```