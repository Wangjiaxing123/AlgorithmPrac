# Description

[98. 验证二叉搜索树 - 力扣（LeetCode） (leetcode-cn.com)](https://leetcode-cn.com/problems/validate-binary-search-tree/)

# Solution

## option 1

对于二叉排序树来说，中序遍历序列为递增有序序列。因此，对给定的二叉树进行中序遍历, 如果能保证前一个值不比后一个值大，则证明该二叉树是一颗二叉排序树

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isValidBST(TreeNode root) {
        return isValidBST(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }
    public boolean isValidBST(TreeNode node, long lower, long upper){
        if(node == null){
            return true;
        }
        if(node.val <= lower || node.val >= upper){
            return false;
        }
        return isValidBST(node.left, lower, node.val) && isValidBST(node.right, node.val, upper);

    }
}
```

