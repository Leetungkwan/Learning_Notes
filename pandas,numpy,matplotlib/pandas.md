## 介绍

- 便捷的数据处理能力
- 读取文件方便
- 封装了 Matplotlib、Numpy 的画图和计算

## 核心数据结构

- DataFrame
- Pannel
- Series

### DataFrame

#### 结构

既有行索引，又有列索引的二维数组

行索引，表明不同行，横向索引，叫 index

列索引，表明不同列，纵向索引，叫 columns

#### 属性

```py
shape # 形状
index # 行索引列表
columns # 列索引列表
values # 直接获取array的值
T      # 矩阵转置
```

#### 方法

```py
head() # 开头几行
tail() # 最后几行
```

#### 索引的设置

```py
# 修改行列索引值 --- 索引不能单独修改，要修改全部

# 重设索引  --- 少用
data.reset_index(drop=False) # drop=True把之前的索引删除

# 设置新索引 --- 常用
data.set_index(keys(索引列表),drop=) # drop=default True---删除原来的列，当作新索引，drop=False，不删除原来的列
```

### Panel    --- 不怎么用，不学

pandas.Panel(data=None,items=None,major_axis=None,minor_axis=None,copy=False,dtype=None)

存储 3 维数组的 Panel 结构

### Series

带索引的一维数组

#### 属性

- index
- values

### 总结

Panel是DataFrame的容器，DataFrame是Series是容器。

### 索引操作

索引分为直接索引（先列后行），按名字索引（loc），按数字索引（iloc）

```py
# 直接索引 --- 少用
data["open"]["2018-02-26"]

# 按名字索引
data.loc["2018-02-26", "open"]
data.loc["2018-02-26"]["open"]

# 按数字索引
data.iloc[1,0]

# 混合索引
loc -- df1.index[数字]
iloc -- df1.columns.get_loc(字符串)
```

### 排序操作

```py
# 对内容进行排序
data.sort_values(by="high", ascending=False) # DataFrame内容排序，by后面填写字段名字，ascending = False表面降序排序

# 对索引进行排序
data.sort_index()
```

### DataFrame运算

```py
# 算术运算
# add(),sub(),或者正常使用就行
data["open"].add(3).head() # open统一加3  data["open"] + 3
```

```py
# 逻辑运算 --- & | > <
# query(expr) expr:查询字符串，有点像SQL语句
data.query("p_change > 2 & low > 15").head()

# isin(values) 判断是否为 values，也是有点像SQL
data[data["turnover"].isin([4.19, 2.39])]
```

```py
# 统计运算 --- 跟numpy里面是差不多的
# describe()函数 --- 能直接获得各列数据的统计值，mean，median，std，var
data.describe()

# 获取最大值
data.max(axis=0)
data.idxmax(axis=0) #最大值位置
```

```py
# 累计统计函数
cumsum 计算前 1/2/3/../n 个数的和
cummax 计算前 1/2/3/../n 个数的最大值
cummin 计算前 1/2/3/../n 个数的最小值
cumprod 计算前 1/2/3/../n 个数的积

# 使用 -- 计算分布函数？？？

data["p_change"].sort_index().cumsum().plot()	
```

```py
# 自定义函数
apply(func, axis=0)
func: 自定义函数

data.apply(lambda x: x.max() - x.min())
```

#### Pandas画图

```markdown
# 主要介绍DataFrame的画图方法
pandas.DataFrame.plot
DataFrame.plot(x=None, y=None, kind='line')

x: label or position, default None
y: label, position or list of label, positions, default None
Allows plotting of one column versus another
kind: str
'line': line plot(default)
''bar": vertical bar plot
"barh": horizontal bar plot
"hist": histogram
"pie": pie plot
"scatter": scatter plot
```

#### 读写csv文件

```py
pd.read_csv("stock_day.csv", usecols=["high", "low", "open", "close"]).head() # 读哪些列
# usecols 表明你需要读入的字段名字

 # 如果列没有列名，用names传入
pd.read_csv("stock_day2.csv", names=["open", "high", "close", "low", "volume", "price_change", "p_change", "ma5", "ma10", "ma20", "v_ma5", "v_ma10", "v_ma20", "turnover"])

 # 保存open列数据 --- 还有很多用法，需要时候再查api使用
data[:10].to_csv("test.csv", columns=["open"])
mode:'w'重写，'a'追加
index：是否写进行索引，布尔类型
header: 是否写进索引值，布尔类型
```

#### 读写hdf5文件

```py
# 二进制文件 -- 读入
data = pd.read_hdf(path,key=)
mode:打开文件模式

# 二进制文件 -- 写入
data.to_hdf(path,key=)
```

#### 读写json文件

```py
# 读取 --- 参数固定
sa = pd.read_json("Sarcasm_Headlines_Dataset.json", orient="records", lines=True)

# 写入 --- 参数固定
sa.to_json("test.json", orient="records", lines=True)
```

