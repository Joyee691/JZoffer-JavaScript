### JZ42和为S的两个数字
> 输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。

#### 双指针
- 思路：利用双指针分别指向数组的首部跟尾部，将他们相加，如果大于sum就将指向尾部的right--、如果小于sum就将指向首部的left++
- 最后返回第一个找到的[right,left]，因为第一个找到的相乘必定是最小的

```
function FindNumbersWithSum(array, sum)
{
    // write code here
    //双指针
    let left=0,
        right=array.length-1;
    
    while(left<right){
        if(array[left]+array[right]===sum)
            return [array[left],array[right]];
        else{
		    if(array[left]+array[right]<sum)
                left++;
            else
                right--;
        }
    }
    return [];
}
```
