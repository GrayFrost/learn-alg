# 移除元素

## Q
给你一个数组 nums 和一个值 val，你需要 原地 移除所有数值等于 val 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 O(1) 额外空间并 原地 修改输入数组。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

示例：
给定 nums = [0,1,2,2,3,0,4,2], val = 2,

函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。

注意这五个元素可为任意顺序。

你不需要考虑数组中超出新长度后面的元素。

## A
``` javascript
var removeElement = function(nums, val) {
    let count = 0;
    for(let i =0; i < nums.length; i++){
        if(nums[i] !== val){
            nums[count] = nums[i];
            count++
        }
    }
    return count
};
```
发现跟上一次做的移除重复元素的题很类似，可以对比总结。