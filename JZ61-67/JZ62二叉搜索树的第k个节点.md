### JZ62二叉搜索树的第k个节点
>给定一棵二叉搜索树，请找出其中的第k小的结点。

#### 递归解法
- 思路：因为二叉搜索树的中序遍历就是递增序列，所以只要使用中序遍历遍历二叉搜索树就可以得到答案，需要注意的是当k==1的时候的节点就是题目要的那个节点，后面的节点可以直接略过

```
/*function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function KthNode(pRoot, k)
{
    // write code here
    let result=null;
    dfs(pRoot);
    return result;
    
    //递归中序遍历，当k等于1时将该节点赋值给result
    //用function声明函数能使声明提前
    function dfs(root){
    		if(!root || k<1)
    			return;
    		dfs(root.left);
    		if(k==1)
    			result=root;
    		if(--k>0)
    			dfs(root.right);
    }
}
```

#### 非递归解法

```
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function KthNode(pRoot, k)
{
    // write code here
    if(!pRoot || k<1)
        return null;
    //使用一个栈模拟递归过程
    const stack=[];
    while(stack.length!=0 || pRoot){
        //将pRoot当前的左子树全部推入stack中
        while(pRoot){
            stack.push(pRoot);
            pRoot=pRoot.left;
        }
        let node=stack.pop();
        if(--k==0)
            return node;
        pRoot=node.right;
    }
}
```
