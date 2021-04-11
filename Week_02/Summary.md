# 哈希表，映射，集合

- HashMap
- HashSet



# 树

与链表的区别： 没有环



## 二叉树遍历

- 前序： 根-左-右
- 中序： 左-根-右
- 后序： 左-右-根

## 模板代码

```java
    public class TreeNode{
        public int val;
        public TreeNode left,right;
        public TreeNode(int val){
            this.val = val;
            this.left = null;
            this.right = null;
        }
    }
```

## 二叉搜索树 binary search tree

也叫二叉排序树，有序二叉树，排序二叉树：是指一颗空树或者具有下列性质的二叉树：

- 左子树上的所有节点的值均小于它的根节点的值；
- 左子树上的所有节点的值均大于它的根节点的值；
- 以此类推：左，右子树也分别为二叉搜索树。

特点：中序遍历为升序排列

### 二叉搜索树常见操作

![image-20210411220305917](http://img.newtrekwang.me/img/20210411220305.png)

（截图来自：https://www.bigocheatsheet.com/）

- 查询 : logn
- 插入新节点
- 删除
- demo: https://visualgo.net/zh/bst

### 树的面试题解法一般都是递归，为什么？

树不方便进行迭代操作，因为它不是一个线性结构。而树的子树就是一个更小规模的树，与递归中子问题的概念完美契合





# 堆

可以迅速找到一推数中的最大或者最小值的数据结构  

- 将根节点最大的堆叫做大顶堆或大根堆
- 根节点最小的堆叫做小顶堆或者小根堆
- 常见的堆有二叉堆，裴波那契堆等

假设是大顶堆，常见操作：

- find-max: O(1)
- delete-max: O(logN)
- insert(create): O(logN) or O()1

不同实现的比较：

## 二叉堆

通过完全二叉树来实现（注意：不是二叉搜索树）

二叉堆（大顶）满足下列性质：

- 是一颗完全树；
- 树中任意节点的值总是大于或等于其子节点的值；

二叉堆的实现细节：

1. 二叉堆一般都通过“数组”来实现
2. 假设“第一个元素”在数组中的索引为0的话，则父节点和子节点的位置关系如下
   - 索引为i的左孩子的索引是（2*i+1）
   - 索引为i的右孩子的索引是（2*i+1）
   - 索引为i的父节点的索引是floor((i-1)/2)
3. Insert 插入操作：
   - 新元素一律先插入到堆的尾部
   - 依次向上调整整个堆的结构（一直到根即可）
4. Delete max 删除堆顶操作
   - 将堆尾元素替换到顶部
   - 依次从根部向下调整整个堆的结构（一直到堆尾即可）

Node: 二叉堆是堆（优先队列priority_queue）的一种常见且简单的实现；但是并不是最优的实现。

# 图

有点有边

- Graph(V,E)
- V-vertex: 点
  - 度 - 入度和出度
  - 点与点之间： 连通与否
- E-edge: 边
  - 有向和无向（单行线）
  - 权重（边长）



# 面试做题步骤

- 1 clarification: 理解并澄清题目
- 2 possible solution --> optimal(time , space)
- 3 code
- 4 test case





# Todo

- 剩下的题

  ![image-20210412014239962](http://img.newtrekwang.me/img/20210412014240.png)

- 看题解，优化代码

- 阅读java源码

