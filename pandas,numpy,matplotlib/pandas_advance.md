## 缺失值处理

- 判断是否有 NaN

  ```py
  pd.isnull(df)
  pd.isnull(df).any() # 用来判断哪一个字段存在缺失值
  
  pd.notnull(df)
  pd.notnull(df).all() # 用来判断哪一个字段存在缺失值
  ```

- 两种处理思路

```py
# 1. 删除数据中含有缺失值的样本 -- 对对象进行处理
df.dropna(inplace=False) # inplace=False不会更改原数据，=True会更改原数据

# 2.替换/插补原数据 -- 对对象进行处理
df.fillna(inplace=False) # inplace=False不会更改原数据，=True会更改原数据
```

### 缺失值不是显示NaN，而是其它符号

```py
# 思路 --- 通过将其它符合转换为NaN，再进行上述处理即可
df.replace(to_replace="", value=np.nan) # to_replace为原来符合，value是改为NaN
```

## 数据离散化 --- 独热码编码

### 过程 --- 注意是对Series类型数据处理

1. 分组

   ```py
   # 自动分组 
   sr = pd.qcut(data, bins)  # bins -- 分成多少组
   
   # 自定义分组 
   sr = pd.cut(data, [])    # [] --- 分组的边界值
   ```

2. 将分组好的结果转换成 one-hot 编码（哑变量）

   ```py
   # 分组后的Series数据的统计
   sr.value_counts()
   
   # 获得独热码
   pd.get_dummies(sr, prefix=)
   ```

## 合并 --- 两个api

```py
# 第一个
pd.concat((data1,data2),axis=0)

# 第二个
pd.merge(left,right,how="inner",on=[索引]) # 用法与数据库一样
```

## 交叉表与透视表 --- 探索两个变量之间的关系

```py
# 第一个
pd.crosstab(value1,value2)

# 第二个
df.pivot_table([], index=["week"])
```

## 分组与聚合

```py
# 纯纯数据库知识 --- 先分组再聚合(没数据库方便和直观)
df.groupby(by=[]).max()

```



