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

#### Decorate Graph
```python
plt.scatter(height_array, weight_array, c="green", marker="+")
plt.title("Height and Weight")
plt.xlabel("Height(cm)")
plt.ylabel("Weight(kg)")
plt.show()
```
![[decorate-graph.png|300]]

#### Sizing Graph
```python
plt.figure(figsize=(10, 4)) 
# set individual

plt.rcParams['figure.figsize'] = (5, 5)
# set all graphs
```