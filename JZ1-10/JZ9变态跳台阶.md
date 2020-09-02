### JZ9变态跳台阶
>一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

- 思路：`f(n)`表示跳上n个台阶的种类数，则`f(n)=f(n-1)+f(n-2)+...+f(0)`是跳上所有其他台阶的可能种类数的总和，且`f(0)=f(1)=1`
- `f(n)=f(n-1)+f(n-2)+...+f(0)`可以简化为`f(n)=f(n-1)*2`

```
function jumpFloorII(number)
{
    // write code here
    if(number==0 || number==1)
        return 1;
    else
        return jumpFloorII(number-1)<<1;
}
```

- 每个楼梯有跳与不跳两种可能，但是最后一个楼梯必跳，所以：<a href="https://www.codecogs.com/eqnedit.php?latex=f(n)=2^{n-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(n)=2^{n-1}" title="f(n)=2^{n-1}" /></a>

```
function jumpFloorII(number)
{
    // write code here
    return Math.pow(2,number-1);
}
```
