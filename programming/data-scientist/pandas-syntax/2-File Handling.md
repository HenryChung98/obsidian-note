### CSV
#### Import
```python
burger_df = pd.read_csv("data/burger.csv")

#if header doesn't exist
burger_df = pd.read_csv("data/burger.csv", header=None, names=['product_name', 'calories', 'carb', 'protein', 'fat', 'sodium', 'category'])

# product name will be column instead number
# if there is a duplicated product name, error
burger_df = pd.read_csv("data/burger/csv", index_col="product_name")
```
#### Export 
```python
# if index isn't set
df.to_csv('data/data1.csv', index=False)
```


## Excel
#### Import
```python
df = pd.read_excel('data/data.xlsx', sheet_name=1, header=1, usecols='B:H')
```
#### Export
```python
# default start row, col is 0
df.to_excel('data/data1.csv', sheet_name='sheet name', startrow=1, startcol=1)
```
