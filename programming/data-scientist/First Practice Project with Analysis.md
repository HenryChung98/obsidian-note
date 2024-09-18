#### Get Data
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('data/jeju_card.csv')

# all data round up by third decimal point
pd.options.display.float_format = '{:.3f}'.format

# search data
df.shape # get row * col
df.info() 
df.describe(include='all')

object_columns = df.columns[df.dtypes == 'object'] # get index
# can be used for for loop
for col in object_columns: 
	print(col) 
	print(df[col].unique(), '\n')

# split and add col
df['year'] = df['연월'].str.split('-').str[0]
```

#### Draw Graph
```python
ym_data = df.groupby('연월').sum(numeric_only=True).reset_index()

sns.barplot(data=ym_data, x='연월', y='이용금액') # 연월 * 이용금액 그래프 그림
plt.rc('font', family='AppleGothic') # 한글이면 이거 필요함
plt.rcParams['figure.figsize'] = (10, 5) # 그래프 사이즈 조정
plt.xticks(rotation=90) # x축 글씨들 90 돌림
plt.title('연월별 카드 이용 금액') # 제목 지정
plt.ylabel('이용금액(억)') # label 지정

# Y축의 값이 너무 크면 씀
# 1억(`100000000`)으로 나눠서, 1억 단위로 볼 수 있도록 
plt.gca().yaxis.set_major_formatter(plt.FuncFormatter(lambda x, _: f'{x/100000000:,.0f}'))
```

#### Sort
```python title:sorted_by_year
order = sorted(df['year'].unique(), reverse=False)
sns.barplot(data=df, x='year', y='이용금액', hue='연령대', order=order)
```

```python title:sorted_by_categories
df['연령대'] = pd.Categorical(jeju_card_df['연령대'], categories=['20대미만', '20대', '30대', '40대', '50대', '60대이상'], ordered=True)

groupby_ym_age = jeju_card_df.groupby(['연도', '연령대']).sum(numeric_only=True).reset_index()
...
```

#### Compare Data
```python
# `year`, `연령대` 두 개의 컬럼을 기준으로 groupby
age_group = df.groupby(['year', '연령대']).sum(numeric_only=True).reset_index()
```

#### Pie Chart
```python
# 연령대별로 나눈 숫자값 데이터 다 가져옴
groupby_age = df.groupby('연령대').sum(numeric_only=True).reset_index()
# 이용자수 %로 나눈 파이차트
groupby_age.plot(kind='pie', y='이용자수', labels=groupby_age['연령대'], autopct='%.1f%%')
# title
plt.title('연령대별 카드 이용자 수 비중')
# legend 위치 조정
plt.legend(loc='upper left', bbox_to_anchor=(1, 1))
```

#### Useful functions
```python title:get_all_unique_index_and_the_values
def print_unique_values(df):
    object_columns = df.columns[df.dtypes == 'object']
    for col in object_columns:
        print(f"{col} unique num: {df[col].nunique()}")
        print(sorted(df[col].unique()), '\n')
```

```python title:combine_multiple_data
# remove trash data
df1 = df1[jeju_reg_18_df['col'] != 'trash data']
df2 = df2[jeju_reg_18_df['col'] != 'trash data']

# concatenate two data
df = pd.concat([df1, df2])

# sanitize
jeju_reg_df['연월'] = jeju_reg_df['연월'].str[:7]
```

```python title:get_top5_index['data']
top5 = groupby_reg.sort_values(by='data', ascending=False).iloc[:5].index

groupby_reg_sec = jeju_reg_df.groupby(['col1', 'col2']).sum(numeric_only=True).reset_index()

for reg in top5:
    reg_df = groupby_reg_sec[groupby_reg_sec['col1'] == reg]
    print(reg, reg_df.sort_values(by='data', ascending=False).iloc[:5]['업종명'].tolist())
```