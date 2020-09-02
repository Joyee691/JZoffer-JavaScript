### JZ14链表倒数第k个节点
> 输入一个链表，输出该链表中倒数第k个结点。

#### 两次循环
- 第一次循环记录链表长度`length`
- 第二次循环返回第`length-k`位
	- 时间复杂度O(2n)：如果k值比较小最坏的情况要遍历两次
	- 空间复杂度O(1)

```
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function FindKthToTail(head, k)
{
    // write code here
    //边界检测
    if(k<0 || head==null)
        return null;
    
    let length=0,
        node=head;
        
    //第一次遍历
    while(node){
        length++;
        node=node.next;
    }
    //边界检测2
    if(k>length)
        return null;
    
    //第二次遍历
    node=head;
    let offset=length-k;
    while(offset--){
        node=node.next;
    }
    return node;
}

```

#### 快慢指针
- 思路：只要将两个指针的距离设置为k，这样当第一个指针指向null的时候第二个指针刚好指向想要的值

```
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function FindKthToTail(head, k)
{
    // write code here
    //边界检测
    if(head==null || k<0)
        return null;
    
    let fast=head,
        slow=head;
    
    //将fast指针调快k步
    for(let i=0;i<k;i++){
        if(fast==null)
            return null;
        fast=fast.next;
    }
    
    while(fast){
        fast=fast.next;
        slow=slow.next;
    }
    
    return slow;
}
```
