# 单变量线性回归 
## 模型描述
1. 房价的训练集 （Training set）
   + notations：
     + m：training examples的数量
     + x：输入变量
     + y：输出变量
     + (x, y)：单个的训练样本，如果表示第i个样本，则在x和y的右上角添加 (i) 来表示
   + 假设函数（Hypothesis）
2. 代价函数（cost function）
   + 假设函数：h(x) = a + bx（对于给定的a和b，h(x)是x的函数）
   + 目标是，找到合适的a和b使得sum( (h(x) - y)^2 )/2m 最小（预测值和实际值差的平方和的平均值最小）
   + 代价函数也叫平方误差函数（squared error function）：J(a, b) = sum( (h(x) - y)^2 )/2m
   + 平方误差函数对大多数回归问题都是一个合适的选择
   + 给定一系列a和b，可以求取对应的J(a, b)，使得J最小的a，b就是最合适的a和b。
3. 梯度下降法（gradient descend：最小化代价函数）
   + 代价函数：J(θ1, θ2, θ3,... θn)
      + 给定一些θi（i=1, 2, 3,...n）的初始值（例如，都设为0）；
      + 逐渐改变θi，以使J逐渐减小，直至找到最小值（局部最小值）。
   + 初始值不同，可能会收敛于不同的局部最优值。
   + 算法：
      + repeat until convergence{
          θi := θi - αdJ/dθi  (for i = 1, 2, 3, ...n)
        }
         + := 表示赋值运算符；
         + α 表示学习率（learning rate）
      + **同时更新所有的θi**  
         ```python
         t0 = theta0 - aJ0'
         t1 = theta1 - aJ1'
         theta0 = t0
         theta1 = t1
         ```
       

   
