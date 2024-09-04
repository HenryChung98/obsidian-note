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
