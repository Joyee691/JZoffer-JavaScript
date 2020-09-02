### JZ7斐波那契数列
> 大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0，第1项是1），n<=39

#### 循环
>时间复杂度O(n)，空间复杂度O(1)

```
function Fibonacci(n)
{
    // write code here
    if(n==0 || n==1)
        return n;
    
    let a=0,
        b=1;
    
    for(let i=2;i<n;i++){
        let c=a+b;
        a=b;
        b=c;
    }
    return a+b;
}
```

#### 递归+动态规划
>时空复杂度O(n)，但是多次调用时速度会快于循环

```
function Fibonacci(n)
{
    // write code here
    const temp={
        0:0,
        1:1
    };
    return fib(n);
    
    function fib(n){
        if(temp[n]!=undefined)
            return temp[n];
        
        temp[n]=fib(n-1)+fib(n-2);
        return temp[n];
    }   
}
```
