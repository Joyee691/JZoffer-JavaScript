> 请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。

#### 正则表达式替换

```
function replaceSpace(str)
{
    // write code here
    if(str.length>=0)
    		return str.replace(/ /g,'%20');
}
```
