**Dataframe删除操作：**

```python
# 删除a行
drop('a')

# 删除a，c行
drop(['a','c'])	

# 删除a，c列
drop(['a','c']，axis = 1)或者drop(['a','c']，axis = 'columns')

# 删除重复行
merged_data = merged_data.drop_duplicates()
```



**遍历列和行：**

```python
# 表示第1列所有数据 
data [:,0]

# 表示第2行所有数据
data [1,:]

# 表示从第2列开始所有数据
data [:, 1:]
```



**更改列名操作：**

```python
# 为序列+原列第二列到最后一列名：
repeated_data.columns = ['序列'] + list(repeated_data.columns[1:])
```



**读取和导入时的操作：**

```python
# header = None表示读取时将第一行的列名视作数据
read_excel(path, header = None)	

# header = False表示导入时不带第一行的列名
to_excel(' ../raw_dataset_excel/AAP.xlsx ',  index = False, header = False)	
```



**loc和iloc：**

```python
# loc基于标签，iloc基于索引

# 表示行标签为0的元素
loc[0]
# 表示列标签为0的元素
loc[:, 0]
# 表示行标签为A，列标签为B的元素
loc["A", "B"]

# 表示第一行
iloc[0]
# 表示第一列
iloc[:, 0]
# 表示第一行第一列
iloc[0, 0]
```



**Pandas Series 对象操作：**

统计某列中每个元素的出现次数，并生成series对象counts：

```python
counts = merged_data['序列'].value_counts()
```

遍历键值对，需要使用 .items() 方法或 .iteritems() 方法来获取元素的键值对。index 表示唯一元素（索引），而 value 表示该元素在第一列中的出现次数（值）：

```python
# 使用迭代器遍历值和索引：

for index, value in counts.items():
    print(f"Element: {index}, Occurrences: {value}")

# 使用 iteritems() 方法：
for index, value in counts.iteritems():
    print(f"Element: {index}, Occurrences: {value}")

```

遍历值：

```python
# 遍历 counts 中的值
for value in counts.values:
    print(f"Occurrences: {value}")
```

将series转换为dataframe:

```python
# 假设da是一个series
df = pd.DataFrame(df)
```



**索引操作：**

```python
# 使用set_index函数将'序列'列设置为索引，如下所示：
merged_data.set_index('序列', inplace=True)

# 重置索引，这个函数会将当前的索引列添加为一个新的列，并将索引重置为默认的整数索引。drop=False表示保留原索引
merged_data.reset_index(inplace=True, drop=False)
```

