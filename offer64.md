# 求1+2+…+n
LeetCode剑指offer第64题

## Q
求 1+2+...+n ，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）

```
输入: n = 3
输出: 6
```

## A
``` javascript
var sumNums = function(n) {
    n && (n += sumNums(n - 1));
    return n;
};
```