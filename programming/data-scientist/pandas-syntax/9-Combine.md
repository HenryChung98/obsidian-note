#### Concatenate
```python
df3 = pd.concat([df1, df2], ignore_index=True)
# 밑으로 붙임

df4 = pd.concat([df1, df2], axis=1)
# 옆으로 붙임(서로 다른 컬럼을 갖고있을때 씀)
```

#### Joins

1. Inner Join: 둘다 있는 데이터만 합침

2. Left Outer Join: 왼쪽 데이터 기준으로 합침(공통으로 있는건 합치고 오른쪽에만 있는건 NaN)

3. Right Outer Join: 오른쪽 데이터 기준으로 합침(공통으로 있는건 합치고 왼쪽에만 있는건 NaN)

4. Full Outer Join: left outer, right outer 합친거

#### Merge
```python
pd.merge(df1, df2, on='id', how='right', suffixes=('_left', '_right'))
# on: id 기준으로 합쳐짐
# how: 4가지 join중 고를 수 있음(inner(default), left, right, outer)
# suffixes: column이 두 데이터에 공통으로 있을때 겹치지 않도록 뒤에 arguments 붙여줌

pd.merge(df1, df2, left_on='id', right_on='another_id')
# 각 데이터에서 key값으로 사용할 column 정함

pd.merge(df1, df2, left_index=True, right_index=True)
# index값을 key값으로 씀(둘 중 하나만 해도 됨)
```

#### Join
```python
df1 = df1.set_index('id')
df2 = df2.set_index('another_id')

df1.join(df2, lsuffix='_x', rsuffix='_y', how='inner')
# df1: left / df2: right
# suffix는 column 겹치면 오류나서 설정해줬음
# how: 4가지 join중 고를 수 있음(inner, left(default), right, outer)

# on='id' 사용 가능
```

