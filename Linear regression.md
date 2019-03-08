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
   
