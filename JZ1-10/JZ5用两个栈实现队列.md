### JZ5用两个栈实现队列
> 用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。

```
//栈：先入后出
//队列：只允许前端删除后段插入
//思路：构建两个栈，分别为inStack与outStack，push()将节点插入inStack，pop()将节点从outStack弹出，当outStack空了的时候，将节点从inStack移到outStack
const inStack=[];
const outStack=[];

function push(node)
{
    // write code here
    inStack.push(node);
}
function pop()
{
    // write code here
    if(!outStack.length){
        while(inStack.length)
            outStack.push(inStack.pop());
    }
    return outStack.pop();
}
```
