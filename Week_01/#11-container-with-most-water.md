# Description

https://leetcode-cn.com/problems/container-with-most-water/

# Solution

# option 1

双指针，夹逼求最大面积

```java
class Solution {
    public int maxArea(int[] height) {
        int left = 0, right = height.length - 1;
        int max = 0;
        while( left < right){
            max = Math.max(max, (right - left) * Math.min(height[left], height[right]));
            if(height[left] < height[right])
            {
                left ++;
            }else{
                right --;
            }
        }
        return max;
    }
}
```

