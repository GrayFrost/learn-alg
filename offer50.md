# 第一个只出现一次的字符
LeetCode剑指Offer第50题

## Q
在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

示例
```
输入：s = "abaccdeff"
输出：'b'
```

## A
```javascript
var firstUniqChar = function(s) {
    const map = new Map();
    for(let char of s) {
        if (map.has(char)) {
            map.set(char, map.get(char) + 1);
        } else {
            map.set(char, 1)
        }
    }
    const entries = map.entries();
    for (const entry of entries) {
        const [char, count] = entry;
        if (count === 1) {
            return char;
        }
    }
    return ' ';
};
```