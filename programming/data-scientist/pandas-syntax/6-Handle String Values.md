#### Upper / Lowercase
```python
# make lowercase
df['data'].str.lower()

# make uppercase
df['data'].str.upper()

# make capitalize
df['data'].str.capitalize()
```

#### Split
```python
# same as python
df['data'].str.split(',')

# get 0th index
df['data'].str.split(',').str[0]


# e.g.
# create first, last columns and insert data, delete name column
df['first'] = df['name'].str.split(',').str[0]
df['last'] = df['name'].str.split(',').str[1]
df = df.drop(columns='name')
```

#### Delete Unnecessary String
```python
# delete white space
df['data'].str.strip()

# replace . to ''
df['data'].str.replace('.', '', regex=False)

# 합쳐서 쓸 수 있음
df['data'].str.strip().str.replace('.', '', regex=False)
```