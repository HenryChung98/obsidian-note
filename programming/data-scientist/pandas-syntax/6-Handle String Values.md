#### Upper / Lowercase
```python
df['data'].str.lower()
# make lowercase

df['data'].str.upper()
# make uppercase

df['data'].str.capitalize()
# make capitalize
```

#### Split
```python
df['data'].str.split(',')
# same as python

df['data'].str.split(',').str[0]
# get 0th index

# e.g.
df['first'] = df['name'].str.split(',').str[0]
df['last'] = df['name'].str.split(',').str[1]
df = df.drop(columns='name')
# create first, last columns and insert data, delete name column
```

#### Delete Unnecessary String
```python
df['data'].str.strip()
# delete white space

df['data'].str.replace('.', '', regex=False)
# replace . to ''

df['data'].str.strip().str.replace('.', '', regex=False)
# 합쳐서 쓸 수 있음
```