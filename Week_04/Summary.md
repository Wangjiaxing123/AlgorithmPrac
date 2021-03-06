# 贪心算法

一种在每一步选择中都采取在当前状态下最好或最优的选择，从而希望导致结果是全局最好的算法。



贪心算法与动态规划的不同在于它对每个子问题的解决方案都做出选择，不能回退。动态规划会保存以前的运算结果，并根据以前的结果对当前进行选择，有回退功能。



# 动态规划

题目特点

- 计数
  - 有多少种方式走到右下角
  - 有多少种方式选出k个数使得和是Sum
- 求最大值和最小值
  - 从左上角走到右下角路径的最大数字和
  - 最长上升子序列长度
- 求存在性
  - 取石子游戏，先手是否必胜
  - 能不能选出k个数使得和是Sum



组成部分：

- 确定状态
  - 最后一步（最优策略中使用的最后一枚硬币ak）
  - 化成子问题(最少的硬币拼出更小的面值27-ak)
- 转移方程
  - 比如f(x) = min{f(x-2)+1, f(x-5)+1, f(x-7)+1}
- 初始条件和边界条件
  - f(0) = 0, 如果不能拼出X, 则f(x)=正无穷
- 消除冗余，加速计算







