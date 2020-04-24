# 搜索插入位置

## Q
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

示例：
```
输入: [1,3,5,6], 5
输出: 2

输入: [1,3,5,6], 2
输出: 1

输入: [1,3,5,6], 7
输出: 4

输入: [1,3,5,6], 0
输出: 0
```
## A
第一种：直接判断
``` javascript
var searchInsert = function(nums, target) {
    if(target < nums[0]){
        return 0
    }
    for(let i = 0; i < nums.length; i++){
      if(nums[i]>=target){
          return i
      }
    }
    return nums.length;
};
```

第二种：二分法
``` javascript
const searchInsert = (nums, target) => {
    let left = 0,
        right = nums.length - 1;
    while (left <= right) {
        let mid = Math.round((left + right) / 2);
        if (nums[mid] === target) {
            return mid;
        } else if (nums[mid] > target) {
            right = mid - 1;
        } else if (nums[mid] < target) {
            left = mid + 1;
        }
    }
    return left;
};
```