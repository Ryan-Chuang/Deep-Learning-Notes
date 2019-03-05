# 机器学习的例子
1. 数据挖掘（网页点击数据，医疗数据，生物，工程等）  
2. 无法手动编程的应用（自动直升机（autonomous helicopter），手写识别(handwriting recognition)，自然语言处理（NLP），计算机视觉）  
3. 自定义程序（self-customizing programs）（亚马逊商品推荐）  
4. 理解人类学习（大脑）  
# 机器学习算法
1. 监督学习（supervised learning）  
   + 给算法一个数据集，其中包含了正确的答案（right answers），算法预测更多的数据集。=> 回归问题（regression problem)
   + 回归问题：预测连续的数值输出（predict continuous valued output）
   + 分类问题（classification problem）：discrete valued output（0, 1 or 2, etc.）
   + 支持向量机（Support Vector Machine）=>无穷多特性输入（attributes）
2. 无监督学习（supervised learning）
   + 无标签（label）的数据集，聚类算法（clustering algorithm）=> 谷歌新闻（新闻专题：cohesive news stories），基因组学。
   + 其他应用：计算机集群（computer clusters）、社交网络分析、市场细分（market segmentation）、天文数据分析。
   + 鸡尾酒聚会问题（cocktail party problem）：
      + Octave编程环境：[W,s,v] = svd((repmat(sum(x.*x,1), size(x,1), 1).*x)*x');
