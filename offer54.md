# 二叉搜索树的第k大节点

LeetCode剑指Offer第54题

## Q
给定一棵二叉搜索树，请找出其中第 k 大的节点的值。

示例
```
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
```

## A
```javascript
var kthLargest = function(root, k) {
    let res;

    dfs(root);
    
    function dfs(root) {
        if (!root) {
            return;
        }
        if(k===0) {
            return;
        }
        dfs(root.right);
        if (--k === 0) {
            res = root.val;
        }
        dfs(root.left)
    }
    return res;
};
```
