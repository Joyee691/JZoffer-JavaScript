> 输入一个链表，按链表从尾到头的顺序返回一个ArrayList

#### 使用unshift

```

/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function printListFromTailToHead(head)
{
    // write code here
    let revArr=[];
    while(head){
        revArr.unshift(head.val);
        head=head.next;
    }
    return revArr;
}

```
