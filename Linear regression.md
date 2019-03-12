# 单变量线性回归 
1. 房价的训练集 （Training set）
   + notations：
     + m：training examples的数量
     + x：输入变量
     + y：输出变量
     + (x, y)：单个的训练样本，如果表示第i个样本，则在x和y的右上角添加 (i) 来表示
   + 假设函数（Hypothesis）
2. 代价函数（cost function）
   + 假设函数：h(x) = θ1 + θ2x（对于给定的θ1和θ2，h(x)是x的函数）
   + 目标是，找到合适的θ1和θ2使得sum( (h(x) - y)^2 )/2m 最小（预测值和实际值差的平方和的平均值最小）
   + 代价函数也叫平方误差函数（squared error function）：J(θ1, θ2) = sum( (h(x) - y)^2 )/2m
   + 平方误差函数对大多数回归问题都是一个合适的选择
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
         + α 表示学习率（learning rate）：太大，则梯度下降会太慢；太小，则梯度下降会过冲最小值，可能无法收敛
         + dJ/dθi表示J对某一个参数θi的偏导数
      + **同时更新所有的θi**  
         ```python
         t0 = theta0 - aJ0'
         t1 = theta1 - aJ1'
         theta0 = t0
         theta1 = t1
         ```
      + 如果θi已经使得J处于最小值，则梯度下降算法应保持θi使得J仍处于最小值。
      + 对梯度下降算法而言，即便学习率固定，其对θi所进行的步进也会随着J的收敛而越来越小。
4. 线性回归的梯度下降法
   + 代价函数：J = sum( (θ1+θ2x - y)^2 )/2m; (x和y取所有训练集)
   + 偏导项： dJ/dθ0 = sum( (h(x) - y)^2 ) / m;   
             dJ/dθ1 = sum( (h(x) - y)^2 ) * x/m;
   + 对于线性回归问题，其代价函数通常呈凸函数类型（convex function）
   + 又称 Batch Gradient Descent
      + 梯度下降的每一个步进都遍历了所有的训练集
   + 正规方程组方法（normal equations methods）可以替代梯度下降法来求解线性回归问题（线性代数知识），但是对于较大的训练集，梯度下降方法更适合。   
# 多变量线性回归
1. 多特征量（Multiple features/variables）
   + 假定特征量的数量是n,则每一个训练集的输入都是一个n维的向量（h(x) = θ1x1 + θ2x2 + ... + θnxn）
   + 向量形式：参数向量Θm = [θ1, θ2, ... , θn]， 特征向量xm = [x1, x2, ... , xn]，则h(x) = transpose(Θm)xm
2. 多元梯度下降法
   + https://github.com/Ryan-Chuang/DL_IMGS/blob/master/%E6%A2%AF%E5%BA%A6%E4%B8%8B%E9%99%8D%E7%AE%97%E6%B3%95.PNG

   
