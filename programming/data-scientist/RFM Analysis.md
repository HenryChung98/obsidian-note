
```python title:컬럼개수_제한_해제
pd.set_option('display.max_columns', None)
```

```python title:convert_birthYear_and_rename
customer_df['birth_year'] = 2024 - customer_df['birth_year']

customer_df = customer_df.rename(columns={'birth_year': 'age'})
```

```python
# 모든 데이터 값 합함
data_amount_total = ( customer_df['amount_alcohol'] + customer_df['amount_fruit'] + customer_df['amount_meat'] + customer_df['amount_fish'] + ...)

# amount general 옆에 amount total insert 함
index_amount_general = customer_df.columns.get_loc('amount_general')

customer_df.insert(loc=index_amount_general + 1, column='amount_total', value=data_amount_total, )
```

RFM 고객 세그먼트 분류
```python
# 1 ~ 3 등급
num_grades = 3
grade_labels = list(range(1, num_grades + 1))

recency_grade = pd.qcut(x=customer_df['recency'], q=num_grades, labels=grade_labels[::-1])


```