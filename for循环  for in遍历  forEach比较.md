# for循环  for in遍历  forEach比较

**一.for**：遍历数组（最原始的写法）

```
//对象
var arr = {A:'a',B:'b',C:'c'};
for(var i=0; i<arr.length; i++){//i是下标（索引）
console.log(i);
console.log(arr[i]);
}
```

结果：

![](F:\Typoraw\imgs\VP64R@GCY16R1]PX~%HAS8W.png)

```javascript
//数组
var arr=["a","b","c"];
for(var i=0; i<arr.length; i++){
    console.log(i);
    console.log(arr[i]);
}
```

结果：

![](F:\Typoraw\imgs\02.png)

**二.for in**:遍历数组（循环数组索引，对象的属性，使用它原型链上的所有的属性都将被访问用hasOwnPrototype（）***总是得到对象的Key或数组，字符串的下标***）

```javascript
//数组
var arr=["a","b","c"];
Array.prototype.more = ["d","e"];
for(var i in arr){
    console.log(arr[i])
}
```

结果：

![](F:\Typoraw\imgs\03.PNG)

```javascript
//对象
var arr = {A:'a',B:'b',C:'c'};
Object.prototype.more = {D:'d'};
for(var i in arr){
    console.log(arr[i]);
}

```

结果：

![](F:\Typoraw\imgs\04.PNG)

```javascript
//索引为字符串类型
var arr=["a","b","c"];
for(var i in arr){
    console.log(typeof i);
    console.log(arr[i]);
}
```

结果：

![](F:\Typoraw\imgs\05.PNG)

```JavaScript
//不是按照书写顺序遍历输出
var obj= {
    name:"lily",
    age:20
}
for(var i in obj){
    console.log(i);//遍历对象的属性
    console.log(obj[i]);//遍历对象的属性值

}
```

结果：

![](F:\Typoraw\imgs\06.PNG)

```javascript
//可拓展属性也会遍历
var arr=["a","b","c"];
arr.name = "lily";
for(var i in arr){
    console.log(i);
    console.log(arr[i]);
}
```

结果：

![](F:\Typoraw\imgs\07.PNG)

**三.forEach**:遍历数组（列出数组的每一个元素，不能用break, continue,return语句；存在低版本兼容问题）

```javascript
//对象
var arr = {A:'a',B:'b',C:'c'};
arr.forEach(function(ele,index,array){//ele当前处理的元素；index此元素下标；array forEach（）操作的数组/对象
    console.log(ele)
    console.log(index)
})
```

