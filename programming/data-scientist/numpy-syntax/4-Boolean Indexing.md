```python
arr1 = np.array([1, 3, 5, 6, 10, 13, 19, 20, 22])
mask = arr1 > 10

print(mask)
# array([False, False, False, False, False,  True,  True,  True,  True])

print(arr1[mask])
# array([13, 19, 20, 22])

print(arr1[(arr1 < 10) | (arr1 > 15)])
# array([ 1,  3,  5,  6, 22])

print(arr1[(arr1 > 10) & (arr1 < 20)])
# array([13, 19])

print(arr1[arr1 % 2 == 0])
# array([ 6, 10, 20, 22])
```
