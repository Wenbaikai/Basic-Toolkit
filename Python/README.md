## 字典反转
```
a = {'John': 60, 'Alice': 95, 'Paul': 80, 'James': 75, 'Bob': 85}

# 问题：如何找出 value = 75 的 key ？

# 方法一：利用 keys() 、values()、index() 函数
name = list(a.keys())[list(a.values()).index(75)]
print(name)   # 输出结果：James

# 方法二：通过列表解析式
name = [key for key, value in a.items() if value == 75]
print(name)   # 输出结果：['James']

# 方法三：将原字典进行反转得新字典
a_inv = {value: key for key, value in a.items()}
print(a_inv[75])   # 输出结果：James
```
