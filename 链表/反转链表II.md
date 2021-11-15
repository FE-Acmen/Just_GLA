## 反转链表II

题目：给你单链表的头指针 head 和两个整数 left 和 right ，其中 left <= right 。请你反转从位置 left 到位置 right 的链表节点，返回 反转后的链表 。

示例：![示例](../assets/images/rev2ex2.jpg)

```
输入：head = [1,2,3,4,5], left = 2, right = 4
输出：[1,4,3,2,5]
```

题解1：利用栈 先进后出

```
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} left
 * @param {number} right
 * @return {ListNode}
 */
var reverseBetween = function(head, left, right) {
    if(head == null) return null;
    let cur = ret = head;
    let stack = [];
    let count = 1;
    while(cur) {
        if(left <= count && count <= right) stack.push(cur.val);
        count++;
        cur = cur.next;
    }

    cur = head;
    count = 1;
    while(cur) {
        if(left <= count && count <= right) cur.val = stack.pop();
        count++;
        cur = cur.next;
    }
    return ret
};
```

