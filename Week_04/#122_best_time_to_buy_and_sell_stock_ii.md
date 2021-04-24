# Description

https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/



# Solution

## 贪心法

```java
class Solution {
    public int maxProfit(int[] prices) {
        // 规律： 只要明天股价比今天高，就可以今天买，明天卖，最后的收益是一样的
        int sum = 0;
        for(int i = 0; i < prices.length - 1; i++){
            if(prices[i + 1] > prices[i]){
                sum += (prices[i + 1] - prices[i]);
            }
        }
        return sum;
    }
}
```

