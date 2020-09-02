### JZ43循环左移字符串ROL
> 汇编语言中有一种移位指令叫做循环左移（ROL），现在有个简单的任务，就是用字符串模拟这个指令的运算结果。对于一个给定的字符序列S，请你把其循环左移K位后的序列输出。例如，字符序列S=”abcXYZdef”,要求输出循环左移3位后的结果，即“XYZdefabc”。

- 思路：只要将字符串“切割开来”，再将头接到尾上就行了

```
function LeftRotateString(str, n)
{
    // write code here
    if(!str)
        return "";
    
    //为了防止n>str.length直接取余数
    n=n%str.length;
    return str.substring(n)+str.substring(0,n);
}
```
