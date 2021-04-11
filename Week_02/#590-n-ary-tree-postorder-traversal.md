# Description

https://leetcode-cn.com/problems/n-ary-tree-postorder-traversal/



# Solution

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> children;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, List<Node> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
    public List<Integer> postorder(Node root) {
        List<Integer> res = new ArrayList<>();
        _postorder(root, res);
        return res;
    }
    public void _postorder(Node root, List<Integer> res){
        if( root == null){
            return;
        }
        for(Node child: root.children){
            _postorder(child, res);
        }
        res.add(root.val);
    }
}
```

