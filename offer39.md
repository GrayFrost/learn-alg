# 数组中出现次数超过一半的数字
LeetCode剑指Offer第39题


## Q
数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

示例：
```
输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
输出: 2
```

## A
```javascript
var majorityElement = function(nums) {
    if (nums.length === 1) {
        return nums[0];
    }
    const map = new Map();
    let target = Math.floor(nums.length / 2);

    for(let i = 0; i < nums.length; i++) {
        if (map.has(nums[i])) {
            const count = map.get(nums[i]) + 1;
            if (count > target) {
                return nums[i];
            }
            map.set(nums[i], count);
        } else {
            map.set(nums[i], 1)
        }
    }
};
```
也可以使用另一种方法：先对数组做排序，然后直接取中位数，此时取的数一定是众数。