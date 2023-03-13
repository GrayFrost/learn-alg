# 从上到下打印二叉树III
LeetCode剑指Offer第32-III题

## Q
请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

例如:
给定二叉树: [3,9,20,null,null,15,7],
```
    3
   / \
  9  20
    /  \
   15   7
```

返回其层次遍历结果：
```
[
  [3],
  [20,9],
  [15,7]
]
```

## A
```javascript
var levelOrder = function(root) {
    if (!root) {
        return [];
    }
    const queue = [root];
    let left = true;
    const res = [];
    while(queue.length) {
        const arr = [];
        let len = queue.length;
        while(len) {
            const current = queue.shift();
            if (left) {
                arr.push(current.val);
            } else {
                arr.unshift(current.val);
            }
            current.left && queue.push(current.left);
            current.right && queue.push(current.right);
            len--;
        }
        left = !left;
        res.push(arr);
    }
    return res;
};
```
