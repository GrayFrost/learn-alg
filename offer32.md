# 从上到下打印二叉树
LeetCode剑指Offer 32 - I

## Q
从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。
例如:
给定二叉树: [3,9,20,null,null,15,7],
```
    3
   / \
  9  20
    /  \
   15   7
```
返回：
```
[3,9,20,15,7]
```

## A
赤裸裸的广度优先遍历
``` javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var levelOrder = function (root) {
    let result = []
    if (!root) {
        return result;
    }
    let queue = [root];
    while (queue.length) {
        let target = queue.shift();
        result.push(target.val);
        target.left && queue.push(target.left);
        target.right && queue.push(target.right);
    }
    return result;
};
```