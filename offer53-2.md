# 0～n-1中缺失的数字
LeetCode 剑指 Offer 53 - II

## Q
一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字

示例
```
输入: [0,1,3]
输出: 2
```

## A
``` javascript
var missingNumber = function(nums) {
    let left = 0;
    let right = nums.length - 1;
    let mid;
    while(left < right){
        mid = Math.floor(left + (right - left) / 2);
        if(nums[mid]===mid){
            left = mid + 1;
        }else{
            right = mid - 1;
        }
    }
    return left;
};
```
使用二分法时，题目中往往会有关键字“排序”
