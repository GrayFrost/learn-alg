# 平衡二叉树
LeetCode 剑指Offer55-II

## Q
输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树。

示例：给定二叉树 [3,9,20,null,null,15,7]
```
    3
   / \
  9  20
    /  \
   15   7
```
返回true。

## A
```javascript
var isBalanced = function(root) {
    if (!root) {
        return true;
    }
    return Math.abs(getHeight(root.left) - getHeight(root.right)) <= 1 && 
        isBalanced(root.left) && 
        isBalanced(root.right);
};

function getHeight(root){
    if (!root) {
        return 0;
    }

    return Math.max(getHeight(root.left), getHeight(root.right)) + 1;
}
```