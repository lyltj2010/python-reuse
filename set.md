
### `Python`里的 `sets`数据类型

`set`是无序`unique`值的集合，常用来去重，检验`membership`等。`set`类似一个词典，但只有键`key`，没有值`value`，好多操作也类似，但不支持索引，切片等操作。


```python
a = set([1,2,3,1])
b = set([2,3,4])
```


```python
a
```




    {1, 2, 3}




```python
print b
```

    set([2, 3, 4])


### 常见操作


```python
a
```




    {1, 2, 3}




```python
len(a)
```




    3




```python
2 in a
```




    True



##### 遍历


```python
# 像遍历字典一样
for i in a:
    print i,
```

    1 2 3


#### 增加


```python
a.add(4)
```


```python
a
```




    {1, 2, 3, 4}



#### 删除


```python
# a.remove(el), if not found, raise error
a.remove(4)
```


```python
a
```




    {1, 2, 3}




```python
# a.discard(el), if not found, do nothing
a.discard(4)
```

#### `pop`


```python
a.pop()
```




    1




```python
a
```




    {2, 3}



#### 交集


```python
a.intersection(b)
```




    {2, 3}



#### 差集


```python
# a - b
a.difference(b)
```




    set()




```python
# b - a
b.difference(a)
```




    {4}



#### 集合关系 


```python
a.issubset(b)
```




    True




```python
b.issuperset(a)
```




    True



#### 清空


```python
a.clear()
```


```python
a
```




    set()


