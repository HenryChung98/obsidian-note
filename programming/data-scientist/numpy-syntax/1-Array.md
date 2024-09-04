```python
arr1 = np.array([1, 3, 5, 6, 7])
# output: array([1, 3, 5, 6, 7])
# shape = (5,)

fill_zeros = np.zeros(5)
# array([0., 0., 0., 0., 0.])

fill_ones = np.ones((2,3))
"""
array([[1., 1., 1.],
       [1., 1., 1.]])
"""

full = np.full((2, 3), 7)
"""
array([[7, 7, 7],
       [7, 7, 7]]
"""

np.arange(2, 17, 3)
# array([ 2,  5,  8, 11, 14])
```

### Indexing
```python
arr1 = np.array([1, 3, 6, 11, 15, 21, 30])

print(arr1[0])
# 1

print(arr1[-1])
# 30

print(arr1[[1, 3, 4]])
# array([ 3, 11, 15])

print(arr1[3:])
# array([11, 15, 21, 30])

print(arr1[1:5])
# array([ 3, 6, 11, 15])

print(arr1[1:-1:2])
# array([ 3, 11, 21])
```


```python
arr1 = np.array([1, 3, 6, 11, 15, 21, 30])
arr2 = np.array([1, 0, 3])

print(arr1[arr2])
# array([3, 1, 11])
```
