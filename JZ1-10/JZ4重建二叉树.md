### JZ4重建二叉树
> 输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。

#### 递归

```
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function reConstructBinaryTree(pre, vin)
{
    // write code here
    //检查是否为空,遍历长度是否一样
    if(!pre.length || !vin.length || pre.length!=vin.length)
        return null;
    // 思路：先序遍历的第一个值是整个树的根节点，在中序遍历中找到根节点左边为左子树右边为右子树，使用递归分别重建左右子树
    const root=pre[0];
    const node=new TreeNode(root);
    
    //借由在中序遍历中找到根节点从而区分左右子树
    let i=0;        //让i的生存域延续到生成子树的时候
    for(;i<pre.length;i++){
        if(vin[i]===root)
            break;
    }
    
    //递归前序遍历与中序遍历的左子树部分
    node.left=reConstructBinaryTree(pre.slice(1,i+1),vin.slice(0,i));
    //递归前序遍历与中序遍历的右子树部分
    node.right=reConstructBinaryTree(pre.slice(i+1),vin.slice(i+1));
    
    return node;
}
```
