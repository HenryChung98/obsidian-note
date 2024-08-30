```python
error_arr = np.array([
		  [1,2,3],
		  [3,4,2],
		  [6,7]
		  ])
# error

arr2 = np.array([
			[1,2,3],
			[3,4,2],
			[6,7,8]
			])
# create 2d list
"""
output
array([[1, 2, 3],
       [3, 4, 2],
       [6, 7, 8]])
"""
# shape = (3, 3)
```

```python
print(arr2[1])
# array([3, 4, 2])

print(arr2[1][2]) # or
print(arr2[1, 2])
# 2

print(arr2[:2, 1:2])
# [[2] [4]]

print(arr2[:, 0:2])
"""
[[1 2]
 [3 4]
 [6 7]]
"""

print(arr2[0:2, :])
"""
[[1 2 3]
 [3 4 2]]
 """
```
