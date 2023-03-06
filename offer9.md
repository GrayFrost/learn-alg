# 用两个栈实现队列
LeetCode剑指Offer第9题

## Q
用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
```
输入：
["CQueue","appendTail","deleteHead","deleteHead","deleteHead"]
[[],[3],[],[],[]]
输出：[null,null,3,-1,-1]

```

## A
```javascript
var CQueue = function() {
    this.inStack = [];
    this.outStack = [];
};

/** 
 * @param {number} value
 * @return {void}
 */
CQueue.prototype.appendTail = function(value) {
    this.inStack.push(value);
};

/**
 * @return {number}
 */
CQueue.prototype.deleteHead = function() {
    if(!this.outStack.length) {
        if(!this.inStack.length) {
            return -1
        }
        while(this.inStack.length) {
            this.outStack.push(this.inStack.pop())
        }
    }
    return this.outStack.pop();
};

```
A栈用来模拟输入，B栈用来实现逆序和删除队列头数据。
比如：
输入5， A[5], B[]，队列[5]
再输入2，A[5, 2], B[]，队列[5,2]
删除队列头5，因为B为空，需要把A的都放到B，A[], B[2,5],此时能删除B的栈顶5,B[2]，队列[2],
再删除队列头，因为B栈还有值，直接删B栈顶。
