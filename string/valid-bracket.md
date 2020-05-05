# 有效的括号

## Q
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

示例 1:
```
输入: "()[]{}"
输出: true
```

示例 2:
```
输入: "(]"
输出: false
```

## A
看过这题的人，应该马上能想到使用栈的思想来解决。
``` javascript
var isValid = function(s) {
    var map = {
        "(": ")",
        "{": "}",
        "[": "]"
    };
    let arr = new Array();
    for(let i = 0; i < s.length; i++){
        let char = s[i];
        if(char in map){
            arr.push(char)
        }else if (map[arr.pop()] !== char){
            return false;
        }
    }
    return !arr.length
};
```