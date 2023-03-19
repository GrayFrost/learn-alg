# 调整数组顺序使奇数位于偶数前面
LeetCode剑指Offer第21题

## Q
输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。

示例：
```
输入：nums = [1,2,3,4]
输出：[1,3,2,4] 
注：[3,1,2,4] 也是正确的答案之一。
```


## A
```javascript
var exchange = function(nums) {
    let left = 0, right = nums.length - 1;
    while (left < right) {
        while(left < right && nums[left] % 2 === 1) {
            left++;
        }
        while(left < right && nums[right] % 2 === 0) {
            right--;
        }
        if (left < right) {
            [nums[left], nums[right]] = [nums[right], nums[left]];
            left++;
            right--;
        }
    }
    return nums;
};
```
双指针，如果左指针不是奇数且右指针不是偶数，交换两个指针数。