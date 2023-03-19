# 和为s的两个数字
LeetCode剑指Offer第57题

## Q
输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

示例
```
输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
```

## A
一、两数之和经典做法，空间复杂度O(n)
```javascript
var twoSum = function(nums, target) {
    const map = new Map();
    for(let i = 0; i < nums.length; i++) {
        if (map.has(target - nums[i])) {
            return [map.get(target - nums[i]), nums[i]]
        } else {
            map.set(nums[i], nums[i]);
        }
    }
    return [];
};
```

二、因为是递增排序数组，使用双指针，将空间复杂度降为O(1)
```javascript
var twoSum = function(nums, target) {
    let left = 0, right = nums.length - 1;
    while(left < right) {
        if (nums[left] + nums[right] === target) {
            return [nums[left], nums[right]];
        } else if (nums[left] + nums[right] < target) {
            left++;
        } else {
            right--;
        }
    }
    return [];
};
```
