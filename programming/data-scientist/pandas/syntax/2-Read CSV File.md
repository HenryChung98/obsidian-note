```python
burger_df = pd.read_csv("data/burger.csv")

#if header doesn't exist
burger_df = pd.read_csv("data/burger.csv", header=None, names=['product_name', 'calories', 'carb', 'protein', 'fat', 'sodium', 'category'])

# product name will be column instead number
# if there is a duplicated name, error
burger_df = pd.read_csv("data/burger/csv", index_col="product_name")


burger_df.iloc[3, 1] # row, col
burger_df.iloc[[2, 3], [1, 2]] # row 2~3, col 1~2
burger_df.iloc[1:4, :3] # row 1~3, col 0~2


burger_df.loc['Double Whopper', 'protein'] 
# get teindouble whopper' protein

burger_df.loc['Double Whopper', 'Whopper', 'protein'] 
# get double whopper, Whopper's protein

burger_df.loc['Double Whopper':'Bacon King', 'protein':'fat']
# same idea

burger_df['calories']
# get all data(burger)'s calories

burger_df['calories'] < 500
# boolean

burger_df.loc[burger_df['calories'] < 500]
# get all data(burger)'s calories less than 500
```


```python
players_df.sort_values(by='matches', ascending=False)
# sort data frame depending on matches

players_df.describe()
# show all data(count, mean, std, max, etc)
```


#### Add, Update Data
```python
burger_df.loc['Cheeseburger'] = [360, 24, 18, 21, 0,7, 'Burger']
# if cheesburger exist, update else add


burger_df['brand'] = 'Burger King'
# add new column(brand) and default value is Burger King

burger_df.loc[burger_df['calories'] >= 500, 'high_calories'] = True
# add high_calories column and insert True if the burger's calories is greater than 500

```

