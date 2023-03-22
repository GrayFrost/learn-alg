# 最小的k个数
LeetCode剑指Offer第40题

## Q
输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

示例：
```
输入：arr = [3,2,1], k = 2
输出：[1,2] 或者 [2,1]
```

## A
```javascript
var getLeastNumbers = function(arr, k) {
    const newArr = arr.sort((a, b) => a - b);
    return newArr.slice(0 , k);
};
```