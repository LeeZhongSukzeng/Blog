# this #

this关键字是JavaScript中最复杂的机制之一。this被自动定义在所有函数的作用域中。

**特点**

函数的调用方式决定了this的值，运行期间绑定

每次函数被调用时this的值也可能会不同

this不能被赋值

this不进行作用域传递

**作用**

复用代码

提供了一个更加优雅而灵便的方案，传递一个隐式的对象引用让代码变得更加简洁。

![1552228279309](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228279309.png)

![1552228287975](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228287975.png)

**绑定规则**

（1）默认绑定

独立函数调用。可以把这条规则看作是无法应用其他规则时的默认规则。函数嵌套时this不进行作用域传递。

使用非严格模式，this会绑定到全局对象window上；使用严格模式，this会绑定到undefined。

![1552228438568](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228438568.png)

![1552228445238](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228445238.png)

（2）隐式绑定

调用位置是否有上下文对象。

函数作为对象的方法调用时，函数上下文指向这个对象。

![1552228584597](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228584597.png)

![1552228593609](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228593609.png)

数组中存放函数，被数组索引调用。this上下文指向这个数组。

![1552228667799](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228667799.png)

就近原则

对象属性引用链中只有最顶层或者说最后一层会影响调用位置。

![1552228745230](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228745230.png)

![1552228751587](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552228751587.png)

（3）显示绑定

使用call（），apply（），bind（）方法显示改变this的指向为指定对象。

（4）new绑定

new来调用函数，或者说发生构造函数调用时，会自动执行下面的操作。

创建，构造一个全新的对象；这个新对象会被执行[[原型]]连接；这个新对象会被绑定到函数调用的this；如果函数没有返回其他对象，那么new表达式中的函数调用会自动返回this（新对象）。

![1552229044682](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552229044682.png)

![1552229049936](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552229049936.png)

![1552229056179](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1552229056179.png)

**绑定优先级**

new绑定>显示绑定> 隐式绑定>默认绑定