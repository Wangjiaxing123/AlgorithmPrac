# Description

https://leetcode-cn.com/problems/reverse-nodes-in-k-group/



# Solution

## option 1

遍历

- 将链表分段
- 对每一段待反转链表进行反转

时间复杂度：O(n)

空间复杂度：O(1)

```java
class Solution {
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode dummy = new ListNode(0, head);
        ListNode pre = dummy, cur = head;
        //计算链表长度
        int length = 0;
        while(head != null){
            head = head.next;
            length++;
        }
        //对链表中每一组的分段
        for(int i = 0; i < length / k; i++){
            //循环将当前分段内的节点反转
            for(int j = 0; j < k - 1; j++){
                ListNode next = cur.next;
                cur.next = next.next;
                next.next = pre.next;
                pre.next = next; 
            }
            //pre后移指向向后面一组待排分段的前一个节点
            pre = cur;
            //cur只需后移一位（即为下一待排分段的第一个节点）
            cur = cur.next;
        }
        return dummy.next;
    }
}
```

