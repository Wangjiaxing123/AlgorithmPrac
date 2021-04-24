# Description



# Solution

## option

# 贪心

只能在特殊情况下通过：

比如硬币值为10,5,1这样的倍数关系可以用贪心

```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        Arrays.sort(coins);
        int count = 0;
        for(int i = coins.length - 1; i >= 0; i--){
            int temp = amount / coins[i];
            if(temp > 0){
                amount = amount - temp * coins[i];
                count += temp;
            }
        }
        return amount == 0 ? count : -1;
    }
}
```

## 动态规划

- 确定状态
  - 最后一步(最优策略中使用的最后一枚硬币ak）
  - 化成子问题(最少的硬币拼出更小的面值27-ak)
- 转移方程: f(x) = min{f(x-2)+1, f(x-5)+1, f(x-7)+1}
- 初始条件和边界条件
  - f(0) = 0, 如果不能拼出X, 则f(x)=正无穷
- 消除冗余，加速计算



```java
class Solution {
    public int coinChange(int[] coins, int amount) {
       // 0,1,...,n n+1
       int[] f = new int[amount + 1];
       // if sum = 0, no coin and f[0] will be used
       f[0] = 0;
       // f(1), f(2), ... f(n)
       for(int i = 1; i <= amount; i++){
           // default, no coin
           f[i] = Integer.MAX_VALUE;
           // f(n) = min{f(n - conin1) + 1, f(n-coin2)+1,...}
           for(int j = 0; j < coins.length; j++){
               // 边界条件： sum值必须答应硬币值, Integer.MAX_VALUE 不能做加法
               if(i >= coins[j] && f[i - coins[j]] != Integer.MAX_VALUE){
                   f[i] = Math.min(f[i], f[i - coins[j]] + 1);
               }
           }
       }
       if(f[amount] == Integer.MAX_VALUE){
           f[amount] = -1;
       }
       return f[amount];
    }
}
```

