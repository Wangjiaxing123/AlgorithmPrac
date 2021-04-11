# Description

https://leetcode-cn.com/problems/two-sum/

# Solution

## option 1

使用 hash 表

时间复杂度：O(N)

空间复杂度：O(N), 主要是哈希表的开销

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for(int i = 0; i < nums.length; i++){
            if(map.containsKey(nums[i])){
                return new int[]{i, map.get(nums[i])};
            }else{
                map.put(target - nums[i], i);
            }
        }
        return new int[0];
    }
}
```

