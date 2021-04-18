# Description

https://leetcode-cn.com/problems/generate-parentheses

# Solution

# option 1

暴力递归

- 先列出所有可能的结果
- 然后筛选出有效的

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList<String>();
        char[] chars = new char[ 2 * n];
        generateAll(chars, 0, list);
        return list;
    }

    public void generateAll(char[] chars, int position, List<String> list){
        if(position == chars.length){
            if(isValid(chars)){
                list.add(new String(chars));
            }
        }else{
            chars[position] = '(';
            generateAll(chars, position + 1, list);
            chars[position] = ')';
            generateAll(chars, position + 1, list);
        }
    }

// 左括号数量必须随时>=0, 然后一直被右括号抵消
    public boolean isValid(char[] chars){
        int leftCount = 0;
        for(char c: chars){
            if(c == '('){
                ++leftCount;
            }else{
                --leftCount;
            }
            if(leftCount < 0){
                return false;
            }
        }
        return (leftCount == 0);
    }
}
```



# Option 2

回溯法

方法一还有改进的余地：我们可以只在序列仍然保持有效时才添加 '(' or ')'，而不是像 方法一 那样每次添加。我们可以通过跟踪到目前为止放置的左括号和右括号的数目来做到这一点，

如果左括号数量不大于 n，我们可以放一个左括号。如果右括号数量小于左括号的数量，我们可以放一个右括号。

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList<String>();
        char[] chars = new char[ 2 * n];
        dfs(chars, 0, 0, 0, n, list);
        return list;
    }

    public void dfs(char[] chars,int current, int left, int right, int max, List<String> list){
        if(left == max && right == max){
            list.add(new String(chars));
            return;
        }
        if(left < max){
            chars[current] = '(';
            dfs(chars, current + 1, left + 1, right, max, list);
        }
        if(right < left){
            chars[current] = ')';
            dfs(chars, current + 1, left, right+1, max, list);
        }
    }
}
```

