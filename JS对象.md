# JS对象 #

**一.JavaScript是一门基于对象的语言**

具有面向对象的一部分特征；在JavaScript中，一切都是对象；某个具体实物（狗）是一个对象（Object）。

**二.对象的属性，行为**

（1）属性：通过变量来表示：var name = “lily”；

（2）行为：通过函数来实现： function jump（）{...}

**三.JavaScript中的对象使用方法**

一系列相关属性和方法的集合，是一种引用数据类型

（1）定义对象

```javascript
var dog = {
    name:"lily";
    weight:60;
    jump: function(){//some action...}
}
```

（2）访问对象属性/方法：通过**对象名.属性名，对象名.方法名（）**；通过**对象名["属性名"]**

![1552805086016](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552805086016.png)

（3）修改对象属性：直接赋值给对象属性。

（4）遍历对象属性

```javascript
for(var i in ObjName){
    //i在循环体内部的每次循环中代表一个属性名
    //通过objName[i]访问到每一个属性
}
```

（5）添加对象属性：为新属性赋值即可

（6）删除对象属性：使用delete关键字

**四.JavaScript包含的对象**

（1）自定义对象：运行中用户自定义JS代码创建的对象



（2）内置对象：由ECMAScript规范定义的对象或构造器对象如：String(var str = new String(""))  ,  Array(同上) , Math （不需创建，直接使用Math.max()）, Date(同上) , Event...



（3）浏览器对象（BOM）



（4）文档对象（DOM）



 （5）宿主对象：由JavaScript解析器所嵌入的宿主环境定义的如window，document。



![1552805032414](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552805032414.png)

**五.对象中数据属性的特性**

（1）**value**（属性的值）：对应属性的值

（2）**writable**(可写特性)：确定属性是否可以改写

（3）**configurable**（可配置性）：确定属性是否能删除和其他特性是否可以配置

（4）**enumerable**（可枚举特性）：属性是否可枚举（影响for-in循环，Object.keys()，JSON.stringify()操作）



例如：一只只读属性的猫

![1552805379402](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552805379402.png)



**六.对象中访问器属性的特征**

（1）**get**:读取属性时调用的函数，该函数计算读取的结果，默认是undefined

（2）**set**：设置属性值时调用的函数，该函数接受设置的值作为参数，默认是undefined

（3）**configurable**

（4）**enumerable**

![1552805851777](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552805851777.png)

![1552805867113](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552805867113.png)

![1552805886827](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552805886827.png)

**七：属性特性的设置**

（1）属性个数为**单数**时：**Object.defineProperty(obj,prop,decriptor)**

obj：要在其上定义属性的对象；prop：要定义或者修改的属性名称；descriptor：将被定义或修改的属性描述符。value默认为undefined，enumerable，writable，configurable默认为false。

![1552806386008](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552806386008.png)

(2)属性个数为**复数**时：**Object.defineProperties(obj,props)**

![1552806414291](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552806414291.png)

**字面量**定义默认属性为**true**

![1552806481376](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552806481376.png)

**八.属性特性的查询**

（1）属性个数为**单数**时：**Object.getOwnPropertyDescriptor(obj,prop)**

obj：需要查找的目标对象；prop：目标对象内属性名称

![1552806623834](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552806623834.png)

(2)属性个数为**复数****时：**Object.getOwnPropertyDescriptors(obj)**

获取一个对象的所有自身属性的描述符

![1552806673115](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552806673115.png)

![1552806678252](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552806678252.png)