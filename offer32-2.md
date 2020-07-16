# 从上到下打印二叉树 II
LeetCode剑指 Offer 32 - II

## Q
从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。
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
  [9,20],
  [15,7]
]
```

## A
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
 * @return {number[][]}
 */
var levelOrder = function(root) {
    if(!root){
        return []
    }
    let result = [];
    let queue = [root];
    let level = 0;
    while(queue.length){
        result[level] = [];
        let levelQueueLength = queue.length;
        while(levelQueueLength>0){
            let target = queue.shift();
            result[level].push(target.val);
            target.left && queue.push(target.left);
            target.right && queue.push(target.right);
            levelQueueLength--;
        }
        level++;
    }
    return result;
};
```