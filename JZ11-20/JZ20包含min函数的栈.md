### JZ20包含min函数的栈
> 定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

#### 直接无脑暴力法
- 注解：竟然过了……

```
let stack=[];

function push(node)
{
    // write code here
    stack.push(node);
}
function pop()
{
    // write code here
    if(stack.length>0)
        stack.pop();
    else 
        return null;
}
function top()
{
    // write code here
    return stack[stack.length-1];
}
function min()
{
    // write code here
    return Math.min(...stack);
}
```

#### 使用辅助数组（辅助栈）
- 思路：既然题目要求要O(1)的时间复杂度，那只能用空间换时间，通过使用一个辅助栈
- 辅助栈功能：
	1. `push`：当要push到原栈的node<=辅助栈的top,同时把node push进辅助栈
	2. `pop`：当要pop的node==辅助栈的top，同时pop辅助栈的top

```
//原来的栈
let stack=[];
//辅助栈
let minStack=[];

function push(node)
{
    // write code here
    stack.push(node);
    if(!minStack.length)
        minStack.push(node);
    else if(node<=minStack[minStack.length-1])
        minStack.push(node);
}
function pop()
{
    // write code here
    if(stack[stack.length-1]===minStack[minStack.length-1]){
        stack.pop();
        minStack.pop();
    }
    else
        stack.pop();
    
}
function top()
{
    // write code here
    return stack[stack.length-1];
}
function min()
{
    // write code here
    return minStack[minStack.length-1];
}
```
