# Description

https://leetcode-cn.com/problems/valid-parentheses/



# Solution

## option 1

利用栈的记录特性，遍历字符数组，如果遇到 '(','[','{'，就push到栈，然后遇到']','}',')'，就pop

```java
class Solution {
    public boolean isValid(String s) {
        if( s == null){
            return false;
        }
        Stack<Character> stack = new Stack<Character>();
        for(char c : s.toCharArray()){
            if(c == '(') stack.push(')');
            else if(c == '[') stack.push(']');
            else if(c == '{') stack.push('}');
            else if(stack.isEmpty() || c != stack.pop()) return false;
        }
        return stack.isEmpty();
    }
}
```



