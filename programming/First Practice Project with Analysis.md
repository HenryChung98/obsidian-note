#### Get Data
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('data/jeju_card.csv')

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


#### Compare Data
```python
# `year`, `연령대` 두 개의 컬럼을 기준으로 groupby
age_group = df.groupby(['year', '연령대']).sum(numeric_only=True).reset_index()
```