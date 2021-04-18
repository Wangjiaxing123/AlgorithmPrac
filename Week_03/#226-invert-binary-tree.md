# Description

[226. 翻转二叉树 - 力扣（LeetCode） (leetcode-cn.com)](https://leetcode-cn.com/problems/invert-binary-tree/)

# Solution

## option 1

递归

- 分解为子问题： 在每个三角，交换左孩子和右孩子，注意空值

```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        reverse(root);
        return root;
    }

    public void reverse(TreeNode root){
        if(root == null){
            return;
        }
        if(root.left == null && root.right == null){
            return;
        }
        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;
        reverse(root.left);
        reverse(root.right);
    }
}



```



优化：

```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return null;
        }
        TreeNode left = invertTree(root.left);
        TreeNode right = invertTree(root.right);
        root.left = right;
        root.right = left;
        return root;
    }
}
```

