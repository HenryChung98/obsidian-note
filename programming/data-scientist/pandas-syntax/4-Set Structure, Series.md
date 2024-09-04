```python
df = df.set_index('id')
# set index column

df = df.reset_index()
# reset index column

df.columns = ['col1', 'col2' ...]
# set columns name


new_columns = {'old': 'new'}
df = df.rename(columns=new_columns)
# rename column refer to dictionary

df = df['data'].astype('float')
# set data type to float
```

```python
df['data'].unique()
# get unique values

df['data'].value_counts()
# get num of each unique value
df['data'].value_counts(dropna=False)
# including NaN

df['data'].value_counts(dropna=False, normalize=True)
# get ratio instead
```