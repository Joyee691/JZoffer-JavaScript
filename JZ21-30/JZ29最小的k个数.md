### JZ29最小的k个数
> 输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4。

- 这题主要考察排序……所以就……

```
function GetLeastNumbers_Solution(input, k)
{
    // write code here
    if(k>input.length || input.length==0)
        return [];
    
    input.sort();
    return input.slice(0,k);
}
```
- 为了防止太水就写几个排序吧……

#### 快速排序

```
function GetLeastNumbers_Solution(input, k)
{
    // write code here
    if(k>input.length || input.length==0)
        return [];
    
    input=fastSort(input);
    return input.slice(0,k);
}

function fastSort(arr){
	if(arr.length<=1)
		return arr;
	let pivot=arr[0];
	let left=[];
	let right=[];
	for(let i=1;i<arr.length;i++){
		if(arr[i]<pivot)
			left.push(arr[i]);
		else
			right.push(arr[i]);
	}
	return fastSort(left).concat([pivot],fastSort(right));
}
```
