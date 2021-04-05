# Description

https://leetcode-cn.com/problems/climbing-stairs/

# Solution

## option 1

```java
class Solution {
    public int climbStairs(int n) {
        if( n <= 3){
            return n;
        }
        int f1 = 1, f2 = 2, f3 = 3;
        for(int i = 3; i <= n; i++){
            f3 = f1 + f2;
            f1 = f2;
            f2 = f3;
        }
        return f3;
    }
}

// f(n) = f(n -1) + f(n -2)
```

