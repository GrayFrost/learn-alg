# 删除链表的节点
LeetCode剑指Offer第18题

## Q
给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。

返回删除后的链表的头节点。

示例
```
输入: head = [4,5,1,9], val = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9.
```

## A
```javascript
var deleteNode = function(head, val) {
    let dummy = new ListNode(-1);
    dummy.next = head;
    let current = dummy;
    while(current.next) {
        const nextVal = current.next.val;
        if (nextVal === val) {
            current.next = current.next.next;
            return dummy.next;
        }
        current = current.next;
    }
    return dummy.next;
};
```
