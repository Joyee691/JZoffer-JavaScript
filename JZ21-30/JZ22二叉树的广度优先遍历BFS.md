### JZ22 二叉树的广度优先遍历BFS
> 从上往下打印出二叉树的每个节点，同层节点从左至右打印。

- 思路：本质上就是BFS的套模版(用pointer取代shift()降低时间复杂度)

```
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function PrintFromTopToBottom(root)
{
    // write code here
    //先进先出的队列
    let queue=[];
    let result=[];
    let pointer=0;
    
    if(root)
        queue.push(root);
    else
        return [];
    
    while(pointer<queue.length){
        let node=queue[pointer++];
        result.push(node.val);
        if(node.left)
            queue.push(node.left);
        if(node.right)
            queue.push(node.right);
    }
    return result;
}
```
