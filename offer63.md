# 股票的最大利润
LeetCode剑指Offer第63题

## Q
假设把某股票的价格按照时间先后顺序存储在数组中，请问买卖该股票一次可能获得的最大利润是多少？

示例
```
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。
```

## A
一、暴力破解
```javascript
var maxProfit = function(prices) {
    let max = 0;
    for(let i = 0; i < prices.length - 1; i++) {
        for (let j = i + 1; j < prices.length; j++) {
            const val = prices[j] - prices[i];
            max = Math.max(max, val);
        }
    }
    return max;
};
```

二、记录历史最小值
```javascript
var maxProfit = function(prices) {
    if (prices.length < 2) {
        return 0;
    }
    let max = 0;
    let min = Number.MAX_VALUE;
    for(const price of prices) {
        max = Math.max(price - min, max);
        min = Math.min(min, price);
    }
    return max;
};
```