# 两数之和

## Q

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍

``` 
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

```

## A

``` javascript
var twoSum = function(nums, target) {

    for (let i = 0, length = nums.length; i < length; i++) {
        for (let j = i + 1, length = nums.length; j < length; j++) {
            if (nums[i] + nums[j] === target) {
                return [i, j]
            }
        }
    }
    return []

};
```

最开始的实现是使用了双重循环，但这种实现的时间复杂度为O(n^2)了😭。

``` javascript
var twoSum = function(nums, target) {

    const map = new Map();
    for (let i = 0, length = nums.length; i < length; i++) {
        let diff = target - nums[i];
        if (map.has(diff)) {
            return [map.get(diff), i]
        }
        map.set(nums[i], i);
    }
    return []

};
```

第二种方法，典型的空间换时间。  
声明一个map变量存储映射结构，以数组值为key，数组下标为value。
比如[1, 2, 3, 4]存到map中为

``` javascript
{
  1: 0, 
  2: 1, 
  3: 2, 
  4: 3
}
```

每次遍历时，查找差值是否已记录在map结构中，在则返回结果，不在则继续存储数组的值。  
比如我的数组为上述的[1, 2, 3, 4]，目标值target为6，当遍历到1时，差值为5，map中没有，存入map，map为{1:0}。
找2时，差值为4，map中没有，存入map，map为{1:0, 2:1}。3同理{1:0, 2:1, 3:2}。当遍历到4时，差值为2，此时map中已有记录，返回map中2对应的value1和遍历时的index3，结束。

