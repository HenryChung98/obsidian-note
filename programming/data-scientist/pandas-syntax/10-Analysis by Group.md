```python
# list, dictionary, dataframe 으로 만들어짐
df.groupby('column_data')

# table로 나옴
df.groupby('column_data').count()
# series로 나옴
df.groupby('column_data').size()

# string도 나옴
df.groupby('column_data').min()
# 숫자만 나옴
# max, mean, sum ...
df.groupby('column_data').min(numeric_only=True)

# data 하나만 계산해 나옴
df.groupby('column_data')['data'].mean()
```


```python
# multi-index
df.groupby(['col1', 'col2'])

# year별로 인덱싱
df.groupby(['year', 'genre']).mean(numeric_only=True)

# genre별로 인덱싱
df.groupby(['genre', 'year']).mean(numeric_only=True)

# 2020년의 모든 데이터 가져옴
df.groupby(['genre', 'year']).mean(numeric_only=True).loc[2020, :]

# get all data of drama, comdey in 2020
df.groupby(['genre', 'year']).mean(numeric_only=True).loc[(2020, ['drama', 'comedy']), :]
```


```python
# 장르별로 평균, 합, 최대값 테이블로 계산해 나옴
df.groupby('genre')['score'].agg(['mean', 'sum', 'max'])

# 평균 score, max, min runtime 가져옴
df.groupby('genre').agg({'score':'mean', 'runtime':['max', 'min']})
```


#### Pivot Table(데이터 요약해서 볼 수 있는 표)
```python
df.groupby(['year', 'genre'])['score'].mean()

pd.pivot_table(df, values='score', index='year', columns='genre', aggfunc='size',).fillna(0).sort_values(by=['col1', 'col2' ...], ascending=False)
# aggfunc default: mean / size: row 개수 세어줌
# fillna: 결측값 0 으로 채움
```

##### 대충 이런 테이블 나옴

| genre    | gen1     | gen2    | gen3    |
| -------- | -------- | ------- | ------- |
| **year** |          |         |         |
| 2019     | 5.652000 | 6.92000 | 6.33000 |
| 2020     | ..       | ..      | ..      |
| 2021     | ..       | ..      | ..      |

#### 시간 간격으로 groupby
```python
df['time_data'] = pd.to_datetime(df['time_data'])
df.set_index('time_data') # datetime이 index로 되있어야 함

# 날짜별로 groupby
# 'Y' = year / 'M' = month
df.resample('D')

# 일별로 sum 구함
df.resample('D').sum(numeric_only=True)
```