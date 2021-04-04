

# Description

https://leetcode.com/problems/reverse-linked-list/

# Solution

## option 1

双指针：

- 定义两个指针： pre 和 cur ；pre 在前 cur 在后。
- 每次让 cur 的 next 指向 pre ，实现一次局部反转
- 局部反转完成之后，pre 和 cur 同时往前移动一个位置
- 循环上述过程，直至 pre 到达链表尾部

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre = null;
        ListNode cur = head;
        while(cur != null){
            // 临时记录下一个节点，使得遍历可以继续
            ListNode tmp = cur.next;
            // 改变 cur 和 pre 之间的关系，使得从 pre -> cur 变成 cur -> pre
            cur.next = pre;
            // pre, cur 都前进一步
            pre = cur;
            cur = tmp;
        }
        return pre;
    }
}
```

时间复杂度：O(n)

空间复杂度：O(1)



## Option 2

递归解法：https://leetcode-cn.com/problems/reverse-linked-list/solution/shi-pin-jiang-jie-die-dai-he-di-gui-hen-hswxy/

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head == null || head.next == null){
            return head;
        }
        ListNode p = reverseList(head.next);
        head.next.next = head;
        head.next = null;
        return p;
    }
}
```

