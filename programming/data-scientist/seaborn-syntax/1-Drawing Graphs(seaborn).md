```python
sns.set_theme(rc={'figure.figsize': (12, 6)}, style='white', font='AppleGothic', palette='pastel') # set theme (set 12inch * 6inch)
sns.barplot(data=df, x='xlabel', y='ylabel', errorbar=None, hue='usually boolean data to compare')
plt.show()
```


```python
# hue: x값에서 여러그룹으로 나눌때
sns.barplot(data=df, x='month', y='total', hue='workingday')
```
![[bar-plot.png|350]]


```python
sns.stripplot(data=df, x='month', y='total', hue='workingday')
```
![[strip-plot.png|350]]


```python
sns.swarmplot(data=df, x='month', y='total', hue='workingday')
```
![[swarm-plot.png|350]]


```python
sns.boxplot(data=df, x='month', y='total', order=[1, 2, 3, 4, 5 ...])
```
![[data-scientist/seaborn-syntax/images/box-plot.png|350]]
```python
sns.violinplot(data=df, x='month', y='total')
sns.histplot(data=df, x='month', y='total', multiple='stack')
sns.scatterplot(data=df, x='month', y='total')
sns.regplot(data=df, x='month', y='total') # 선을 그리고 상관관계 분석

df.corr(numeric_only=True) # 상관계수 확인
sns.heatmap(df.corr(numeric_only=True), annot = True) # 색으로 상관계수 구분
```