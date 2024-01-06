## 介绍

基本操作
    ndarray.方法()
    numpy.函数名()
ndarray运算
    逻辑运算
    统计运算
    数组间运算

numpy可以处理任意维数组（nd.array）

### 优势

1. 存储风格
   - ndarray - 相同类型 - 通用性不强
   - list - 不同类型 - 通用性很强
2. 并行化运算
   - ndarray 支持向量化运算
3. 底层语言
   - Numpy 底层使用 C 语言编写，内部解除了 GIL（全局解释器锁），其对数组的操作速度不受 Python 解释器的限制，效率远高于纯 Python 代码。

## 属性

| 属性名字          | 属性解释                   |
| ----------------- | -------------------------- |
| **ndarray.shape** | 数组维度的元组             |
| ndarray.ndim      | 数组维数                   |
| ndarray.size      | 数组中的元素数量           |
| ndarray.itemsize  | 一个数组元素的长度（字节） |
| **ndarray.dtype** | 数组元素的类型             |

## 基本操作

1. 生成0和1的数组

```python
np.zeros(shape,dtype=)  # 生成形状是shape，类型是dtype的全0数组
np.ones(shape,dtype=)  # 生成形状是shape，类型是dtype的全1数组
```

2. 从现有数组生成

```py
data1 = np.asarray() # 浅拷贝
data2 = np.array()   # 深拷贝
data3 = np.copy()    # 深拷贝
```

3. 生成固定范围的数组

```py
np.linspace(0,10,5) # 生成[0,10]之间等距离的五个数
np.arange(0,11,5)   # 生成[0,11)，5为步长的是数组
```

4. 生成随机数组

```py
# 生成均匀分布的一组数[low,high)
data1 = np.random.uniform(low=-1, high=1,size=100000)
# 生成正态分布的一组数，loc：均值；scale：标准差
data2 = np.random.normal(loc=1.75,scale=0.1,size=100000)
```

5. 形状修改

```py
# 注意是对对象进行处理
ndarray.reshape(shape) # 返回新的ndarray，原始数据没有改变
ndarray.resize(shape)  # 没有返回值，对原始的ndarray进行了修改
ndarray.T # 对数据进行了转置，返回新的ndarray，原始数据没有改变
```

6. 类型修改

```py
# 对对象进行处理
ndarray.astype("type(int32)")  # 常用，记忆，不改变原对象
ndarray.tostring() # 序列化本地，不知道什么用处
```

7. 数组去重

```py
ndarray = [[1,2,3,4],[3,4,5,6]]
temp = np.array(ndarray)  
np.unique(temp)  # 会被降维处理
```

8. ndarray的运算

### 逻辑运算

```py
# 运算符
# 逻辑判断, 如果涨跌幅大于0.5就标记为True 否则为False
stock_change > 0.5
stock_change[stock_change > 0.5] = 1.1
```

```py
# 通用判断符，与SQL语言作对比
# 判断stock_change[0:2, 0:5]是否全是上涨的
np.all(stock_change[0:2, 0:5] > 0)
# 判断前5只股票这段期间是否有上涨的
np.any(stock_change[:5, :] > 0)
```

```py
# 三元运算符
# np.where(布尔值，True的位置的值，False的位置的值)
np.where(temp > 0, 1, 0)
# 大于0.5且小于1
np.where(np.logical_and(temp > 0.5, temp < 1), 1, 0)
# 大于0.5或小于-0.5
np.where(np.logical_or(temp > 0.5, temp < -0.5), 11, 3)
```

### 统计指标函数

```py
# 两种使用方法
1. np.函数名
2. ndarray.方法名
函数：min，max，median，var，std
temp.max(axis=0) # axis指定维度名字，对于二维数组来说，axis=0意味着对列进行操作，axis=1意味着对行进行操作
np.max(temp,axis=1) # axis指定维度名字
```

```py
# 返回最大值，最小值的位置
np.argmax(temp,axis)
np.argmin(temp,axis)
```

```py
# 数组与数的运算 --- 跟正常的数学思维一样
# 数组与数组的运算 --- 要满足广播机制
```

```py
# 矩阵运算 --- 矩阵是二维数组，但二维数组不是矩阵
# np.mat() --- 可将ndarray转换成矩阵
# 矩阵的相乘
# 1. 若为matrix形状，满足乘法规则下，直接相乘
# 2. 若为ndarray形状
nd.matmul(ndarray1,ndarray2) # 由matrix 和 multiple 两个单词组成
nd.dot(ndarray1,ndarray2)    # 点乘的意思，顾名思义
```

### 合并与分割

这两个用法很少使用，基本上都用pandas实现

```py
# 合并
np.hstack((ndarray1,ndarray2)) # 水平拼接
np.vstack((ndarray1,ndarray2))  # 竖直拼接
np.concatenate((ndarray1,ndarray2),axis=) # axis=0是竖直拼接，axis=1是水平拼接
```

```
# 分割
np.split(x,3) # 分成三份
np.split(x,[3,4,6,10]) # 按索引分割
```



