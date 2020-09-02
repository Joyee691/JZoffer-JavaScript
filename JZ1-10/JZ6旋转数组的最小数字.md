## JZ6旋转数组的最小数字
>把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。
>输入一个非递减排序的数组的一个旋转，输出旋转数组的最小元素。
>例如数组{3,4,5,1,2}为{1,2,3,4,5}的一个旋转，该数组的最小值为1。
>NOTE：给出的所有元素都大于0，若数组大小为0，请返回0。

- 非递减排序定义：arr[n+1]>=arr[n]
- 思路：
	1. `arr[mid]<arr[end]`:表示数组右边是递增排列，如{5,6,1,2,3,4}，这种状况只需要考虑左边[start,mid]范围就好
	2. `arr[mid]>arr[end]`:表示数组经过数次旋转，如{3,4,5,6,1,2},这种情况只需要考虑(mid,end]范围就好
	3. `arr[mid]==arr[end]`:表示数组可能有相同数字，如{2,2,2,1,2,2},这种情况需要考虑[start,end-1]范围
	4. `arr[start]<arr[end]`:表示整个数组都是递增数列，直接返回arr[start]就好


```
function minNumberInRotateArray(rotateArray)
{
    // write code here
    if(!rotateArray.length)
        return 0;

    let start=0;
    let end=rotateArray.length-1;
    
    //循环到最后只有一个数字的时候退出
    while(start<end){
        let mid=(end+start)>>1;
        
        //如果是递增数组则直接返回第一位
        if(rotateArray[start]<rotateArray[end])
            return rotateArray[start];
        
        if(rotateArray[mid]<rotateArray[end])
            end=mid;
        else if(rotateArray[mid]>rotateArray[end])
            start=mid+1;
        else 
            end--;
    }
    return rotateArray[start];
}    

```		
