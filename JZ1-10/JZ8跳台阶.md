### JZ8跳台阶
> 一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。

- 思路：`F(n)`表示跳上n个台阶的可能数，则`F(n)=F(n-1)+F(n-2)`本质上是斐波那契数列数列，但是F(0)=1,F(1)=1，所以要求jumpFloor(n)实际上是求Fib(n+1)

```
function jumpFloor(number)
{
    // write code here
    if(number<=1)
        return 1;
    
    let a=1,b=1,c;
    while(--number){
        c=a+b;
        a=b;
        b=c;
    }
    return c;
}
```
