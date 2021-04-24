# Description

https://leetcode-cn.com/problems/lemonade-change/

# Solution

## 贪心

```java
class Solution {
    public boolean lemonadeChange(int[] bills) {
        if(bills.length == 0){
            return false;
        }
        // 只能从小额开始收钱，不然没零钱
        if(bills[0] > 5){
            return false;
        }
        // 每次收钱时，能不能凑钱补零钱
        // 记录硬币数
        int f5 = 0, f10 = 0, f20 = 0; 
        for(int i = 0; i < bills.length; i++){
            if(bills[i] == 5){ // 遇到付5元的
                f5+=1;
            }else if(bills[i] == 10){// 遇到付10元的
                if(f5 == 0){
                    return false;
                }else{
                    f5 -= 1;
                    f10+=1;
                }
            }else{ // 遇到付20元的
                // 最优： 有大头的就先补大头
                if(f10 > 0 && f5 > 0){
                    f10 -= 1;
                    f5 -= 1;
                }else if(f10 == 0 && f5 >= 3){
                    f5 -= 3;
                }else{
                   return false;
                }
            }
        }
        return true;
    }
}
```

