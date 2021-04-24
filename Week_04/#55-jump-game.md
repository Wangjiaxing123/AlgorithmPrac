# Description

https://leetcode-cn.com/problems/jump-game/



# Solution

贪心法： 从终点反推，只要能到达终点就是可行的

```java
class Solution {
    public boolean canJump(int[] nums) {
        if(nums.length == 1){
            return true;
        }
        int reach = nums.length - 1;
        for(int i = reach - 1; i >= 0; i--){
            // 如果从当地位置(i)出发, 跳nums[i]步能达到终点(reach), 那么更新终点为当前位置
            if( i + nums[i] >= reach){
                reach = i;
            }
        }
        return reach == 0;
    }
}
```

