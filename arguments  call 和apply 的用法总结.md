# arguments  call（） 和apply（）bin（） 的用法总结 #

**1.arguments用法**（JavaScript的内置对象，每一个函数都有arguments关键字）

​    （1）在函数调用时，可以用来输出实参的集合，应为有时传递的实参个数不一定等于形参个数，所以用arguments方法可以知道实际的实参个数。

```javascript
//输出实参个数
function fun(a,b){
    console.log(a);
    console.log(b);
    console.dir(arguments);
}
fun(1,2,3);

//Arguments(3)
0:1
1:2
2:3
```

```javascript
//找到最大的一个参数值
x = findMax(1, 123, 500, 115, 44, 88);
 
function findMax() {
    var i, max = arguments[0];
    
    if(arguments.length < 2) return max;
 
    for (i = 0; i < arguments.length; i++) {
        if (arguments[i] > max) {
            max = arguments[i];
        }
    }
    return max;
}

```

```JavaScript
//求和

x = sumAll(1, 123, 500, 115, 44, 88);
 
function sumAll() {
    var i, sum = 0;
    for (i = 0; i < arguments.length; i++) {
        sum += arguments[i];
    }
    return sum;
}

```

（2）arguments.length

​                 arguments.length的值只与传入的实参有关系。在函数调用时，实参的个数确定所以arguments.length也确定，不会再发生改变。

```JavaScript
 //arguments 的 length 的值
        function fun(a, b, c) {
            console.log(arguments.length);//2
            arguments[4] = 1;
            console.log(arguments.length);//2   // arguments只与传入的实参有关系
            return a + b;
        }
        var obj = { x: 1, y: 2 };
        fun(1, obj);
        console.log(obj); //{ x: 2,y: 3}

```

（3）arguments与形参的“双向绑定”特征

​                  向函数传递参数时，arguments数组中的对应单元会和命名参数建立关联以得到相同的值，相反，不传递参数就不会建立联系。







**2.call（） apply（）bin（）用法**（函数对象中的方法）

```JavaScript
var name ="小王",age=17;
var obj={
    name:"小张",
    objAge:this.age,
    myFun:function(){
        console.log(this.name+"年龄"+this.age);
    }
}
var db={
    name:"德玛",
    age:99
}

obj.myFun.call(db)；　　　　// 德玛年龄 99
obj.myFun.apply(db);　　　 // 德玛年龄 99
obj.myFun.bind(db)();　　　// 德玛年龄 99


```

以上出了 bind 方法后面多了个 () 外 ，结果返回都一致！

由此得出结论，bind 返回的是一个新的函数，你必须调用它才会被执行。

```javascript
var name ="小王",age=17;
var obj={
    name:"小张",
    objAge:this.age,
    myFun:function(fm,t){
        console.log(this.name+"年龄"+this.age,"来自" + fm +"去往" +t);
    }
}
var db={
    name:"德玛",
    age:99
}

obj.myFun.call(db,'成都','上海')；　　　　 // 德玛 年龄 99  来自 成都去往上海
obj.myFun.apply(db,['成都','上海']);      // 德玛 年龄 99  来自 成都去往上海  
obj.myFun.bind(db,'成都','上海')();       // 德玛 年龄 99  来自 成都去往上海
obj.myFun.bind(db,['成都','上海'])();　　 // 德玛 年龄 99  来自 成都, 上海去往 undefined
```

​     call 、bind 、 apply 这三个函数的第一个参数都是 this 的指向对象，第二个参数差别就来了：

call 的参数是直接放进去的，第二第三第 n 个参数全都用逗号分隔，直接放到后面  obj.myFun.call(db,'成都', ... ,'string' )。

apply 的所有参数都必须放在一个数组里面传进去 obj.myFun.apply(db,['成都', ..., 'string' ])。

bind 除了返回是新函数以外，它 的参数和 call 一样。