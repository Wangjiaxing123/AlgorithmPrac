# Description

https://leetcode-cn.com/problems/bulls-and-cows/



# Solution

## option 1

迭代

迭代一次，如果相同位置上数字相同，则bull++, 如果不同则记录两字符串里数字出现的次数，最后对比两个记录，如果数字次数都>0，则表示两字符串都含有该数字，则cow++

时间复杂度：O(N)

```java
class Solution {
    public String getHint(String secret, String guess) {
        char[] secretNumberCount = new char[10];
        char[] guessNumberCount = new char[10];
        int A = 0;
        for(int i = 0; i < secret.length(); i++){
            if(secret.charAt(i) == guess.charAt(i)){
                A++;
            }else{
                secretNumberCount[secret.charAt(i) - '0']++;
                guessNumberCount[guess.charAt(i) - '0']++;
            }
        }

        int B = 0;
        for( int j = 0; j < 10; j++){
            B += Math.min(secretNumberCount[j], guessNumberCount[j]);
        }
        return ""+ A + "A" + B +"B";
    }
}
```

