### Get Data
iloc: based on integer
loc: based on label
```python
burger_df.iloc[3, 1] # row, col
burger_df.iloc[[2, 3], [1, 2]] # row 2~3, col 1~2
burger_df.iloc[1:4, :3] # row 1~3, col 0~2

# get double whopper's protein
burger_df.loc['Double Whopper', 'protein'] 
# get double whopper, Whopper's protein
burger_df.loc['Double Whopper', 'Whopper', 'protein'] 
# same idea
burger_df.loc['Double Whopper':'Bacon King', 'protein':'fat']

# get all data(burger)'s calories
burger_df['calories']
# boolean
burger_df['calories'] < 500

# get all data(burger) depending on the condition
burger_df[burger_df['calories'] < 500]
# get all data(burger)'s protein only depending on the condition
burger_df.loc[burger_df['calories'] < 500, 'protein']
```


### Add, Update Data
```python
# if cheesburger exist, update else add
burger_df.loc['Cheeseburger'] = [360, 24, 18, 21, 0,7, 'Burger']

# add new column(brand) and default value is Burger King
burger_df['brand'] = 'Burger King'

# add high_calories column and insert True if the burger's calories is greater than 500
burger_df.loc[burger_df['calories'] >= 500, 'high_calories'] = True
```


### Delete Data
```python
burger_df.drop('index id')

burger_df.drop(columns='column name')

burget_df.drop('index id', axis=1)
# axis: column
```