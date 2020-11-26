# 顺时针打印矩阵
LeetCode剑指offer第29题。

## Q
输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]

## A
```javascript
var spiralOrder = function(matrix) {
    if(!matrix || matrix.length === 0){return []}
    let arr = [];
    
    let left = 0, right = matrix[0].length - 1,
    top = 0, bottom = matrix.length - 1;
    while(left < right && top < bottom){
        for(let i = left; i < right; i++){
            arr.push(matrix[top][i])
        }
        for(let i = top; i < bottom; i++){
            arr.push(matrix[i][right])
        }
        for(let i = right; i > left; i--){
            arr.push(matrix[bottom][i])
        }
        for(let i = bottom; i > top; i--){
            arr.push(matrix[i][left])
        }
        left++;
        right--;
        top++;
        bottom--;
    }
    if(top === bottom && left < right){
        for(let i = left; i < right;i++){
            arr.push(matrix[top][i])
        }
    }
    if(left === right && top < bottom){
        for(let i = top; i < bottom; i++){
            arr.push(matrix[i][left])
        }
    }
    if(left === right && top === bottom){
        arr.push(matrix[top][left])
    }
    return arr;
};
```