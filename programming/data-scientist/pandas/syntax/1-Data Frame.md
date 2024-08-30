```python
df = pd.DataFrame({
    'category': ['skirt', 'sweater', 'coat', 'jeans'],
    'quantity': [10, 15, 6, 11],
    'price': [30, 60, 95, 35]
})

print(df)
```

| category | quantity | price |
|----------|----------|-------|
| skirt    | 10       | 30    |
| sweater  | 15       | 60    |
| coat     | 6        | 95    |
| jeans    | 11       | 35    |

```python
print(df['quantity'])
```

| 0   | 10  |
| --- | --- |
| 1   | 15  |
| 2   | 6   |
| 3   | 11  |
Name: quantity, dtype: int64


```python
print(df['quantity'] * df['price'])
```

| Index | Value |
|-------|-------|
| 0     | 300   |
| 1     | 900   |
| 2     | 570   |
| 3     | 385   |
dtype: int64


```python
print(df['quantity'].mean())
# 10.5

print(df['quantity'].sum())
# 42
```


#### Using Numpy
```python
two_dimensional_list = [ 
				['skirt', 10, 30000], 
				['sweater', 15, 60000], 
				['coat', 6, 95000], 
				['jeans', 11, 35000] 
				]
				
two_dimensional_array = np.array(two_dimensional_list)

list_df = pd.DataFrame(two_dimensional_list, columns=['category', 'quantity', 'price']) 
array_df = pd.DataFrame(two_dimensional_array, columns=['category', 'quantity', 'price'])
```

| category | quantity | price |
| -------- | -------- | ----- |
| skirt    | 10       | 30    |
| sweater  | 15       | 60    |
| coat     | 6        | 95    |
| jeans    | 11       | 35    |

