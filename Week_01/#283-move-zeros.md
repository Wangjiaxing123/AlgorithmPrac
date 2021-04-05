# Description



# Solution

## option 1

双指针，先遍历出所有不等于0的数，直接从头覆盖写入，最后剩下的覆盖为0

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int j = 0;
        for(int i = 0; i < nums.length; i++){
            if(nums[i] != 0){
                nums[j++] = nums[i];
            }
        }
        while(j < nums.length){
            nums[j++] = 0;
        }
    }
}
```

