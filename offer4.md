# 二维数组中的查找
LeetCode剑指offer第4题

## Q
在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数

现有矩阵 matrix 如下：
```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
```
给定 target = 5，返回 true。

给定 target = 20，返回 false

## A
```javascript
var findNumberIn2DArray = function(matrix, target) {
    if(matrix === null || matrix.length === 0){
        return false;
    }
    let rows = matrix.length;
    let columns = matrix[0].length;
    let currentRow = 0,currentColumn = matrix[0].length - 1;
    while(currentRow < rows && currentColumn < columns){
        let current = matrix[currentRow][currentColumn];
        if(current === target){
            return true
        }else if(current > target){
            currentColumn--;
        }else{
            currentRow++;
        }
    }
    return false;
};
```
从二维数组的右上角开始查找，如果当前值大于目标值，往左；如果当前值小于目标值，往下。
