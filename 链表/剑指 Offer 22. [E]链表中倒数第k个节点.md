### [剑指 Offer 22\. 链表中倒数第k个节点](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

Difficulty: **简单**


输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。

例如，一个链表有 `6` 个节点，从头节点开始，它们的值依次是 `1、2、3、4、5、6`。这个链表的倒数第 `3` 个节点是值为 `4` 的节点。

**示例：**

```
给定一个链表: 1->2->3->4->5, 和 k = 2.

返回链表 4->5.
```


#### Solution

Language: **java**



方法1

```java
class Solution {
    public ListNode getKthFromEnd(ListNode head, int k) {
        ListNode h1 = head;
        k -= 1;
      	// 因为没有头部节点，第k个元素，真跳转到该数据，需要进行减一操作
        while(k-- > 0) {
            h1 = h1.next;
        }
        ListNode h2 = head;
        while(h1.next != null) {
            h1 = h1.next;
            h2 = h2.next;
        }
        return h2;
    }
}
```



方法2

```java
class Solution {
    public ListNode getKthFromEnd(ListNode head, int k) {
        // 先跳k步
        ListNode dummp = new ListNode(-1);
        dummp.next = head;
        ListNode cur = dummp;
        while(k-- > 0) {
            cur = cur.next;
        }
        ListNode pos = dummp;
        while(cur != null) {
            pos = pos.next;
            cur = cur.next;
        }
        return pos;
    }
}
```

