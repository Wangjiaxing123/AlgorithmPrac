# Description

https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/



# Solution

## option 1

暴力，每次滑动都求它的最大值

```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
       if(nums.length == 1 || nums.length == 0){
           return nums;
       }
       int left = 0;
       int right = k - 1;
       int resultLength = nums.length - k + 1;
       int[] result = new int[resultLength];
       for(int i = 0; i < resultLength; i++){
           result[i] = findMax(nums, left + i, right + i);
       }
       return result;
    }

    public int findMax(int[] nums, int left, int right){
        int max = nums[left];
        for(int i = left; i <= right; i++ ){
            max = max < nums[i] ? nums[i] : max;
        }
        return max;
    }
}
```

## option 2

利用单调递减队列：

https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/solution/dong-hua-yan-shi-dan-diao-dui-lie-jian-z-unpy/



```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
       if(nums.length == 1 || nums.length == 0){
           return nums;
       }
       int left = 0;
       int right = k - 1;
       int resultLength = nums.length - k + 1;
       int[] result = new int[resultLength];
       Deque<Integer> queue = new LinkedList<>();
       for(int i = 0, j = 0; i < nums.length; i++){
           // 队列里的第一个数是最大的，如果它的下标已超出窗口范围，则弹出
           if( !queue.isEmpty() && i - queue.peek() >= k){
                queue.poll();
           }
           // 如果当前值大于队列里最后个值，则弹出，使得队列里的值成递减
           while(!queue.isEmpty() && nums[i] > nums[queue.peekLast()]){
               queue.pollLast();
           }
           // 将当前值推入队列
           queue.offer(i);
           // 当前队列第一个值则为当前窗口最大值
           if( i >= k - 1){
               result[j++] = nums[queue.peek()];
           }
       }
       return result;
    }
}
```

