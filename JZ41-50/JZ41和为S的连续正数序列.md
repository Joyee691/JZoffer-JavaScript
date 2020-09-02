### JZ41和为S的连续正数序列
>找出所有和为S的连续正数序列  
>输出描述:输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序

#### 滑动窗口
- 思路：使用两个指针left与right分别指向窗口的左边与右边，然后计算窗口中的总和tmp，此时tmp有三种可能性：
	1. tmp<sum:这个时候就把right往右+1，把窗口增大
	2. tmp>sum:这时候就把left往右+1，把窗口缩小
	3. tmp==sum:这时候就把窗口中的值push到result中
- 终止条件，当左窗口超过sum的一半时，因为在这种情况下任何两个数相加一定大于sum
	- 时间复杂度O(n)


```
function FindContinuousSequence(sum)
{
    // write code here
    let result=[],        //储存所有结果
        left=1,        //左窗口
        right=1,        //右窗口
        tmp=0;        //储存当时窗口的总和
    
    while(left<Math.ceil(sum/2)){
        if(tmp<sum){
            tmp+=right;
            right++;
        }else if(tmp>sum){
            tmp-=left;
            left++;
        }else{
            let ans=[];
            for(let i=left;i<right;i++)
                ans.push(i);
            result.push(ans);
            tmp-=left;
            left++;
        }
    }
    return result;
}
```
