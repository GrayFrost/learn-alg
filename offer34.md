# 二叉树中和为某一值的路径
LeetCode剑指Offer第34题

## Q
给你二叉树的根节点 root 和一个整数目标和 targetSum ，找出所有 从根节点到叶子节点 路径总和等于给定目标和的路径。
叶子节点 是指没有子节点的节点。

![示例](./image/offer34/1.jpeg)
```
输入：root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
输出：[[5,4,11,2],[5,8,4,5]]

```

## A
```javascript
var pathSum = function(root, target) {
    const res = [];

    dfs(root, target, []);
    function dfs(root, target, path){
        if (!root) {return;}
        path.push(root.val);

        if (target === root.val && !root.left && !root.right) {
            res.push(path.slice());
        }
        dfs(root.left, target - root.val, path);
        dfs(root.right, target - root.val, path);
        path.pop();
    }
    return res;
};
```