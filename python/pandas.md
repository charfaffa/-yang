### dataframe.reset_index(drop=False)
drop默认参数是False，就是将原来的索引变成默认的整数索引列，drop参数就是决定是否删除原来的索引列
如果是True就将原来的索引丢弃。
### 在去重后索引会发生变化，即便是默认的索引
```python
import pandas as pd

# 创建一个示例 DataFrame
df = pd.DataFrame({'A': [1, 2,2,3,3], 'B': [4, 5, 6,3,3]})
df.drop_duplicates(subset=['A'],inplace=True,keep='last')
df
#输出
	A	B
0	1	4
2	2	6
4	3	3