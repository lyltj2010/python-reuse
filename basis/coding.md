
## 字符编码

[参见原文](http://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/001386819196283586a37629844456ca7e5a7faa9b94ee8000#0)。

因为计算机只能处理数字，如果要处理文本，就必须先把文本转换为数字才能处理。

由于计算机是美国人发明的，因此，最早只有`127`个字母被编码到计算机里，也就是大小写英文字母、数字和一些符号，这个编码表被称为`ASCII`编码，比如大写字母`A`的编码是`65`，小写字母z的编码是`122`。

但是要处理中文显然一个字节是不够的，至少需要两个字节，而且还不能和`ASCII`编码冲突，所以，中国制定了`GB2312`编码，用来把中文编进去。

日本把日文编到`Shift_JIS`里，韩国把韩文编到`Euc-kr`里，各国有各国的标准，还有完没完？！

因此，`Unicode`应运而生。`Unicode`把所有语言都统一到一套编码里，这样就不会再有乱码问题了。捋一捋`ASCII`编码和`Unicode`编码的区别：`ASCII`编码是`1`个字节，而`Unicode`编码通常是`2`个字节。

如果统一成`Unicode`编码，乱码问题从此消失了。但是，如果你写的文本基本上全部是英文的话，用`Unicode`编码比`ASCII`编码需要多一倍的存储空间，在存储和传输上就十分不划算。  

所以，本着节约的精神，又出现了把`Unicode`编码转化为“可变长编码”的`UTF-8`编码。`UTF-8`编码把一个`Unicode`字符根据不同的数字大小编码成`1-6`个字节，常用的英文字母被编码成`1`个字节，汉字通常是`3`个字节，只有很生僻的字符才会被编码成`4-6`个字节。如果你要传输的文本包含大量英文字符，用`UTF-8`编码就能节省空间。

在计算机**内存**中，**统一使用`Unicode`编码**，当需要**保存到硬盘**或者需要**传输**的时候，就转换为`UTF-8`编码。

比如用记事本编辑的时候，从文件读取的`UTF-8`字符被转换为`Unicode`字符到内存里，编辑完成后，保存的时候再把`Unicode`转换为`UTF-8`保存到文件。  

![unicode<->utf-8](http://www.liaoxuefeng.com/files/attachments/001387245992536e2ba28125cf04f5c8985dbc94a02245e000/0)



又比如浏览网页的时候，服务器会把动态生成的`Unicode`内容转换为`UTF-8`再传输到浏览器。  

所以你看到很多网页的源码上会有类似<meta charset="UTF-8" />的信息，表示该网页正是用的UTF-8编码。  

![unicode<->utf-8](http://www.liaoxuefeng.com/files/attachments/001387245979827634fd6204f9346a1ae6358d9ed051666000/0)

### `ASCII`字母数字互换


```python
ord('A')
```




    65




```python
chr(65)
```




    'A'



### `Unicode` vs `UTF-8`


```python
# python unicode
print u'中'
u'中' # unicode 
```

    中
    u'\u4e2d'




```python
'中' # utf-8，每个字一般对应三个字节
```


    '\xe4\xb8\xad'



### 转为`UTF-8`  

用**`encode('utf-8')`**，把`Unicode`编码为`utf-8`。


```python
u'A'.encode('utf-8')
```


    'A'


```python
u'中'.encode('utf-8')
```


    '\xe4\xb8\xad'


英文字符转换后表示的`UTF-8`的值和`Unicode`值相等（但占用的存储空间不同），而中文字符转换后`1`个`Unicode`字符将变为`3`个`UTF-8`字符，你看到的`\xe4`就是其中一个字节，因为它的值是`228`，没有对应的字母可以显示，所以以十六进制显示字节的数值。


```python
len(u'A')
```


    1


```python
len('A')
```


    1


```python
len(u'中')
```


    1


```python
len('中')
```


    3


```python
len('\xe4\xb8\xad')
```


    3

### 转为`Unicode`

用**`decode('utf-8')`**，把`utf-8`解码为`Unicode`。


```python
'A'.decode('utf-8')
```


    u'A'


```python
print '\xe4\xb8\xad'.decode('utf-8')
'\xe4\xb8\xad'.decode('utf-8')
```

    中
    u'\u4e2d'


```python
'中'.decode('utf-8')
```


    u'\u4e2d'


### 常用代码


```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
```


```python
import sys
reload(sys)
sys.setdefaultencoding('UTF-8')
```
