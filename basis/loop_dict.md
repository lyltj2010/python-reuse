
## 遍历字典


```python
d = {'x': 1, 'y': 2, 'z': 3}
```

### 遍历keys


```python
for key in d:
    print key,
```

    y x z



```python
for key in d.iterkeys():
    # d.iterkeys(): an iterator over the keys of d
    print key,
```

    y x z



```python
for key in d.keys():
    # d.keys() -> ['y', 'x', 'z']
    print key,
```

    y x z


### 遍历values


```python
for value in d.itervalues():
    # d.itervalues: an iterator over the values of d
    print value,
```

    2 1 3



```python
for value in d.values():
    # d.values() -> [2, 1, 3]
    print value,
```

    2 1 3


### 遍历keys和values


```python
for key, value in d.iteritems():
    # d.iteritems: an iterator over the (key, value) items
    print key,'corresponds to',d[key]
```

    y corresponds to 2
    x corresponds to 1
    z corresponds to 3



```python
for key, value in d.items():
    # d.items(): list of d's (key, value) pairs, as 2-tuples
    # [('y', 2), ('x', 1), ('z', 3)]
    print key,'corresponds to',value
```

    y corresponds to 2
    x corresponds to 1
    z corresponds to 3

