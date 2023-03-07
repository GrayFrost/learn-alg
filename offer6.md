# 从尾到头打印链表
LeetCode剑指Offer第6题

## Q
输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

```
输入：head = [1,3,2]
输出：[2,3,1]
```

## A
```javascript
/**
 * @param {ListNode} head
 * @return {number[]}
 */
var reversePrint = function(head) {
    if (!head) {
        return [];
    }
    let current = head;
    let arr = [];
    while(current) {
        arr.unshift(current.val);
        current = current.next;
    }
    return arr;
};
```