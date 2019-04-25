# Basics
1. 改变一个张量的操作，通常在关键词后面添加一个 ```_```。如：  
    ```y.add_(x)```  
    ```a.requires_grad_(True)```
2. ```torch.autograd```是计算矢量-夹可比矩阵积的方法。
    + 如果v=dl/dy(l是y的标量函数)，而J=dy/dx（y是x的矢量函数），那么矢量-夹可比矩阵积就恰好是：J^T * v =dl/dx;
3. 由于pylint的问题，torch在pylint检查时，常常会报“module torch has no ** member”的错误，解决办法如下：
    + click on File > Preferences > Settings.
    + search “Mypy Args”
    + click on "Edit in settings.json" link
    + edit the json to include: ```"python.linting.pylintArgs": ["----extension-pkg-whitelist=1xml"]```
4. Loss.backward()对于Loss是一个标量的时候，其第一个参数即```gradient```可以无需指定，但如果Loss是一个多维矢量，则需要指定一个与之维度一致的tensor。如：
    ```python
    import torch
    m = torch.tensor([2, 3], dtype = torch.float, requires_grad=True)
    j = torch.zeros(2 ,2)
    k = torch.zeros(2)

    k[0] = m[0] ** 2 + 3 * m[1]
    k[1] = m[1] ** 2 + 2 * m[0]
    
    grad_tensor = torch.FloatTensor([1, 1])     #维度与k一致，是1x2的tensor
    k.backward(grad_tensor)
    print(m.grad.data)
    ```
    上述代码输出为```tensor([6., 9.])```。这是由于，grad_tensor的第一个元素，指定对m[0]反向求导，并将求导的结果与grad_tensor的第一个元素相乘；由于autograd具有累加性质，所以最终的结果是dk0/dm0 + dk1/dm0 = 4 + 2 = 6；同理，第二个元素求导的结果是dk0/dm1 + dk1/dm1 = 3 + 6 = 9;   
    **假设 x 经过一番计算得到 y，那么 y.backward(w) 求的不是 y 对 x 的导数，而是 l = torch.sum(y*w) 对 x 的导数。w 可以视为 y 的各分量的权重，也可以视为遥远的损失函数 l 对 y 的偏导数（这正是函数说明文档的含义）。特别地，若 y 为标量，w 取默认值 1.0，才是按照我们通常理解的那样，求 y 对 x 的导数。**
