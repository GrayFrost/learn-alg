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
    let max = 0;
    function dfs(root, count = 0){
        if (!root) {
            return;
        }
        count++;
        max = Math.max(count, max);
        root.left && dfs(root.left, count);
        root.right && dfs(root.right, count);
        count--;
    }
    dfs(root);
    return max;
};
```

方法二：递归
``` javascript
var maxDepth = function (root) {
  if(!root) {
    return 0;
  }
  return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1;
}
```
方法三：广度优先遍历，即层次遍历
LeetCode第104题一样的，我用广度优先实现了。思路是之前在做从上到下打印二叉树中学来的。