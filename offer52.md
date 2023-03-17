# 两个链表的第一个公共节点
LeetCode剑指Offer第52题

## Q
输入两个链表，找出它们的第一个公共节点。
如下面的两个链表：
![图](./image/offer52/1.png)

在节点 c1 开始相交。

## A
```javascript
var getIntersectionNode = function(headA, headB) {
    if (headA === null || headB === null) {
        return null;
    }
    let nA = headA, nB = headB;
    while (nA !== nB) {
        nA = nA === null ? headB : nA.next;
        nB = nB === null ? headA : nB.next;
    }
    return nA;
};
```
交换跑道，浪漫相遇。
A遍历完后遍历B，B遍历完后遍历A。如果有公共节点，则一定会相遇。