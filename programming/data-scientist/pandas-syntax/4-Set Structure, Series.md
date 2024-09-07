```python
# set index column
df = df.set_index('id')

# reset index column
df = df.reset_index()

# set columns name
df.columns = ['col1', 'col2' ...]


new_columns = {'old': 'new'}
# rename column refer to dictionary
df = df.rename(columns=new_columns)

# set data type to float
df = df['data'].astype('float')
```

```python
# get unique values
df['data'].unique()

# get num of each unique value
df['data'].value_counts()

# including NaN
df['data'].value_counts(dropna=False)

# get ratio instead
df['data'].value_counts(dropna=False, normalize=True)
```