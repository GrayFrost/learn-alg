# 二叉树的深度
LeetCode剑指 Offer 55 - I

## Q
输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。
例如：

给定二叉树 [3,9,20,null,null,15,7]，
```
    3
   / \
  9  20
    /  \
   15   7
```
返回它的最大深度 3 。

## A
方法一：深度优先遍历
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
 * @return {number}
 */
var maxDepth = function (root) {
    if (!root) {
        return 0;
    }
    let depth = 0;
    let stack = [root];
    function dfs(node, dep) {
        dep += 1;
        if (!node.left && !node.right) {
            depth = Math.max(depth, dep)
        }
        node.left && dfs(node.left, dep);
        node.right && dfs(node.right, dep);
    }
    dfs(root, 0)
    return depth;
};
```

方法二：递归
方法三：广度优先遍历，即层次遍历