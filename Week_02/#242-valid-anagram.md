# Description

https://leetcode-cn.com/problems/valid-anagram/



# Solution

## option 1

使用hash表

key 为 char

value 为 出现个数

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length()){
            return false;
        }
        char[] sChars = s.toCharArray();
        char[] tChars = t.toCharArray();
        HashMap<Character, Integer> map = new HashMap<>();
        for(int i = 0; i < sChars.length; i++){
            Integer count = map.get(sChars[i]);
            if(count == null){
                map.put(sChars[i], 1);
            }else{
                map.put(sChars[i], ++count);
            }
        }
        for(int i = 0; i < tChars.length; i++){
            Integer count = map.get(tChars[i]);
            if(count != null){
                if(count == 1){
                    map.remove(tChars[i]);
                }else{
                    map.put(tChars[i], --count);
                }
            }
        }
        return map.isEmpty();
    }
}
```

优化：

因为是小写字母，字符总共就26个，所以可以用一个size为26的数组来实现hash表

index 为字符的int值-'a'

value 为出现字符的个数



时间复杂度：O(n)

空间复杂度：O(n)

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length()){
            return false;
        }
        char[] sChars = s.toCharArray();
        char[] tChars = t.toCharArray();
        int[] simpleTable = new int[26];
        for(int i = 0; i < sChars.length; i++){
            int indexS = sChars[i] - 'a';
            simpleTable[indexS] ++;
            int indexT = tChars[i] - 'a';
            simpleTable[indexT] --;
        }
        for(int i = 0; i < simpleTable.length; i++){
           if(simpleTable[i] != 0){
               return false;
           } 
        }
        return true;
    }
}
```

