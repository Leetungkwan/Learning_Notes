# 时刻与matlab比较

## 三层结构

### 容器层

1. 画板层（canvas）
2. 画布层（figure）
3. 绘图区（subplots）

### 辅助显示层

## 图像层

## 画图三件套

```py
plt.figure()   para有figsize（图像大小），dpi（清晰度）
plt.plot(x,y)
plt.show()
## 对x的处理，遵循先用数字生成坐标，再用xticks对其进行描述
```

## 添加刻度

```py
plt.xticks(x,**kwargs) # 对x的刻度进行操作
plt.yticks(y,**kwargs) # 对y的刻度进行操作
```

## 添加网格

```py
plt.grid(True,linestyle = '--', alpha = 0.5)
```

## 添加坐标描述和标题

```py
plt.xlabel()
plt.ylabel()
plt.title()
```

## 添加图例

```py
plt.legend()
```

## 解决中文显示问题

```py
# 配置中文字体
plt.rcParams['font.sans-serif'] = [u'SimHei']
plt.rcParams['axes.unicode_minus'] = False
```

## 绘制多个绘图区

```py
fig, axes = plt.subplots(nrows=1,ncols=1,**fig_kw)
# axes的方法有所不同，最大的区别是其需要加一个前缀“set_”
```

## 绘制散点图

```py
plt.scatter(x, y)
```

## 绘制柱状图

```py
plt.bar(x,y,width,label)
```

## 绘制直方图

```py
plt.hist(x,bins=None,density=None)
# x表示横坐标，bins表示组数，dengsity表示是否生成频率分布直方图
```

## 绘制饼图

```py
plt.pie(x,labels=,autopct=,colors=)
'''
x:数量
labels：每部分的描述
autopct：占比显示格式（一般为%1.2f%%）
colors：每部分颜色
'''

plt.axis('equal') # 与横纵坐标相匹配
```

