#### Line Graph
```python
year_array = np.array([2011, 2012, 2013, 2014, 2015, 2016])
stock_array = np.array([14.46, 19.01, 20.04, 27.59, 26.32, 29.96])

plt.plot(year_array, stock_array)
plt.show()
```
![[plot-graph.png|300]]

#### Bar Graph
```python
name_array = np.array(['a', 'b', 'c', 'd', 'e'])
vote_array = np.array([3, 5, 1, 10, 7])

plt.bar(name_array, vote_array)
plt.show()
```
![[bar-graph.png|300]]

#### Scatter Graph
```python
height_array = np.array([165, 164, 155, 151, 157, 162, 155, 157])
weight_array = np.array([62, 59, 57, 55, 60, 58, 51,56])

plt.scatter(height_array, weight_array)
plt.show()
```
![[scatter-graph.png|300]]

#### Box Plot
```python
df = pd.read_csv('data/test_school.csv')
df['english_score'].plot(kind='box')
plt.show()
```
![[data-scientist/seaborn-syntax/images/box-plot.png|575]]


#### Histogram(범위별로 나누는 그래프)
e.g. 150~160 / 160~170 / 170~180...
```python
df['height'].plot(kind='hist', bins=10) # bins: num of graph bar
plt.show()
```


#### Kernel  Density Estimation Plot(Histogram을 세밀하게 표현한 그래프)
```python
df['height'].plot(kind='kde', bw_method=0.1) # bw_method: 분포를 얼마나 세세하게 표현할지
plt.show()
```