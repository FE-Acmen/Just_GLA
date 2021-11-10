## 删除链表的倒数第N个节点

题目： 给你一个链表，删除链表的倒数第 `n` 个结点，并且返回链表的头结点 。

![示例](../assets/images/remove_ex1.jpg)

```
输入：head = [1,2,3,4,5], n = 2
输出：[1,2,3,5]
```

题解：

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    // 双指针
    let ret = new ListNode(undefined, head)
    let p1 = ret, p2 = ret;
    for(let i=0;i<n;i++) {
        p1 = p1.next;
    }
    while (p1.next != null) {
        p1 = p1.next;
        p2 = p2.next;
    }
    p2.next = p2.next.next;
    return ret.next;
};
```

