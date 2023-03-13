# 二叉树的镜像
LeetCode剑指Offer第27题

## Q
请完成一个函数，输入一个二叉树，该函数输出它的镜像。
例如输入：

     4
   /   \
  2     7
 / \   / \
1   3 6   9
镜像输出：

     4
   /   \
  7     2
 / \   / \
9   6 3   1

## A
```javascript
var mirrorTree = function(root) {
    if (!root) {
        return null;
    }
    const left = mirrorTree(root.left);
    const right = mirrorTree(root.right);
    root.left = right;
    root.right = left;
    return root;
};
```