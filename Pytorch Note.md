# Basics
1. 改变一个张量的操作，通常在关键词后面添加一个 ```_```。如：  
  ```y.add_(x)```  
  ```a.requires_grad_(True)```
2. ```torch.autograd```是计算矢量-夹可比矩阵积的方法。
  + 如果v=dl/dy(l是y的标量函数)，而J=dy/dx（y是x的矢量函数），那么矢量-夹可比矩阵积就恰好是：J^T * v =dl/dx;
