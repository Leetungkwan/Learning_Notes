# 函数 是指一段可以直接被另一段程序调用的程序或代码。

使用语句：`select 函数` 

## 字符串函数

|           函数           | 功能                                                      |
| :----------------------: | --------------------------------------------------------- |
|   concat(S1,S2,...Sn)    | 字符串拼接，将S1，S2，... Sn拼接成一个字符串              |
|        lower(str)        | 将字符串str全部转为小写                                   |
|        upper(str)        | 将字符串str全部转为大写                                   |
|     lpad(str,n,pad)      | 左填充，用字符串pad对str的左边进行填充，达到n个字符串长度 |
|     rpad(str,n,pad)      | 右填充，用字符串pad对str的右边进行填充，达到n个字符串长度 |
|        trim(str)         | 去掉字符串头部和尾部的空格                                |
| substring(str,start,len) | 返回从字符串str从start位置起的len个长度的字符串           |

## 数值函数

|    函数    | 功能                               |
| :--------: | ---------------------------------- |
|  ceil(x)   | 向上取整                           |
|  floor(x)  | 向下取整                           |
|  mod(x,y)  | 返回x//y                           |
|   rand()   | 返回0~1内的随机数                  |
| round(x,y) | 求参数x的四舍五入的值，保留y位小数 |

## 日期函数

|                函数                | 功能                                              |
| :--------------------------------: | ------------------------------------------------- |
|             curdate()              | 返回当前日期                                      |
|             curtime()              | 返回当前时间                                      |
|               now()                | 返回当前日期和时间                                |
|             year(date)             | 获取指定date的年份                                |
|            month(date)             | 获取指定date的月份                                |
|             day(date)              | 获取指定date的日期                                |
| date_add(date, INTERVAL expr type) | 返回一个日期/时间值加上一个时间间隔expr后的时间值 |
|       datediff(date1,date2)        | 返回起始时间date1 和 结束时间date2之间的天数      |

## 流程函数

|                            函数                            | 功能                                                     |
| :--------------------------------------------------------: | -------------------------------------------------------- |
|                       if(value,t,f)                        | 如果value为true，则返回t，否则返回f                      |
|                   ifnull(value1,value2)                    | 如果value1不为空，返回value1，否则返回value2             |
|    case when [val1] then [res1] ... else [default] end     | 如果val1为true，返回res1，...否则返回default默认值       |
| case [expr] when [val1] then [res1] ... else [default] end | 如果expr的值等于val1，返回res1，...否则返回default默认值 |

## 窗口函数

特点：`group by`分组汇总后改变了表的行数，一行只有一个类别。而`partiition by`和`rank`函数不会减少原表中的行数。

```mysql
<窗口函数> over (partition by <用于分组的列名>
                order by <用于排序的列名>)
```

| 函数         | 功能                                     |
| ------------ | ---------------------------------------- |
| rank()       | 如果有并列名次的行，会占用下一名次的位置 |
| dense_rank() | 如果有并列名次的行，不占用下一名次的位置 |
| row_number   | 不考虑并列名次的情况                     |


