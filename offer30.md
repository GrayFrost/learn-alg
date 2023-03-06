# 包含min函数的栈
LeetCode剑指Offer第30题

## Q
定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

示例
```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.

```

## A
```javascript
/**
 * initialize your data structure here.
 */
var MinStack = function() {
    this.stack = [];
    this.minStack = [Infinity];
};

/** 
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function(x) {
    this.stack.push(x);
    this.minStack.push(Math.min(x, this.minStack[this.minStack.length - 1]));
};

/**
 * @return {void}
 */
MinStack.prototype.pop = function() {
    this.stack.pop();
    this.minStack.pop();
};

/**
 * @return {number}
 */
MinStack.prototype.top = function() {
    if (this.stack.length) {
        return this.stack[this.stack.length - 1];
    }
    return -1;
};

/**
 * @return {number}
 */
MinStack.prototype.min = function() {
    if (this.minStack.length) {
        return this.minStack[this.minStack.length - 1];
    }
    return -1;
};
```
首先多构造个辅助栈，用来从最小值。在每一次原始栈入值时，辅助的最小栈也同样存值，存的是入栈值和已存最小值的比较值。
比如现存-2
A [-2]
B [Infinity, -2]

再存0,0和-2比，-2更小
A [-2, 0]
B [Infinity, -2, -2]

再存-3,-3比-2小
A [-2, 0, -3]
B [Infinity, -2, -2, -3]。即每次栈顶都是存最小值。