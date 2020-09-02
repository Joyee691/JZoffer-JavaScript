>在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

#### 暴力解法

```
function Find(target, array)
{
	//检查第一维数组的长度
    const row=array.length;
    if(row==0)    
        return false;
        
     //检查第二维数组的长度
    const col=array[0].length;
    if(col==0)
        return false;
        
     //暴力轮询   
    for(let i=0;i<row;i++){
        for(let j=0;j<col;j++){
            if(array[i][j]===target)
                return true;
        }
    }
    return false;
}
```
#### 二分查找求解

```
function Find(target, array)
{
    // write code here
    const rowNum=array.length;
    if(rowNum==0)    
        return false;
    const colNum=array[0].length;
    if(colNum==0)
        return false;
    //从数组的最后一行开始找，如果小于则搜索上一行，如果大于则往右搜索
    let row=rowNum-1,
        col=0;
    while(row>=0&&col<colNum){
        if(array[row][col]===target)
            return true;
        else if(target<array[row][col])
            row--;
        else if(target>array[row][col])
            col++;
    }
    return false;
}

```
