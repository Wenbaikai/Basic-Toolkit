## torch.split()

   torch.split()作用将tensor分成块结构。

参数：

· tesnor：input，待分输入

· split_size_or_sections：需要切分的大小(int or list )

· dim：切分维度

· output：切分后块结构 <class 'tuple'>

```
当split_size_or_sections为int时，tenor结构和split_size_or_sections，正好匹配，那么ouput就是大小相同的块结构。
如果按照split_size_or_sections结构，tensor不够了，那么就把剩下的那部分做一个块处理。
import torch
 
x = torch.rand(4,8,6)
y = torch.split(x,2,dim=0) #按照4这个维度去分，每大块包含2个小块
for i in y :
    print(i.size())
 
output:
torch.Size([2, 8, 6])
torch.Size([2, 8, 6])
 
y = torch.split(x,3,dim=0)#按照4这个维度去分，每大块包含3个小块
for i in y:
    print(i.size())
 
output:
torch.Size([3, 8, 6])
torch.Size([1, 8, 6])
-------------------------------------------------------------
当split_size_or_sections 为list时，那么tensor结构会一共切分成len(list)这么多的小块，每个小块中的大小按照list中的大小决定，
其中list中的数字总和应等于该维度的大小，否则会报错（注意这里与split_size_or_sections为int时的情况不同）。
import torch
 
x = torch.rand(4,8,6)
y = torch.split(x,[2,3,3],dim=1)
for i in y:
    print(i.size())
 
output:
torch.Size([4, 2, 6])
torch.Size([4, 3, 6])
torch.Size([4, 3, 6])
 
 
y = torch.split(x,[2,1,3],dim=1) #2+1+3 等于6 != 8 ,报错
for i in y:
    print(i.size())
 
output:
split_with_sizes expects split_sizes to sum exactly to 8 (input tensor's size at dimension 1), but got split_sizes=[2, 1, 3]
```
