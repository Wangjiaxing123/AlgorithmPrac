# Description

https://leetcode-cn.com/problems/assign-cookies/



# Solution

## option 1

贪心法：

```java
class Solution {
    // 贪心法：每次寻找最优
    // 每次分的时候，为了充分利用，尽量先要小的满足胃口小的
    // 确定下这两个数组是不是已经排好序的
    public int findContentChildren(int[] g, int[] s) {
        if(s.length == 0){
            return 0;
        }
        Arrays.sort(g);
        Arrays.sort(s);
        int count = 0;
        int j = 0;
        for(int i = 0; i < g.length; i++){
            for(; j < s.length; j++){
                if(g[i] <= s[j]){
                    count++;
                    j++;
                    break;
                }
            }
        }
        return count;
    }
}
```

