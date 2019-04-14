# Ajax与JSON 

**JSON**（Javascript  Object Notation，JS对象标记）

JSON是Javascript对象的字符串形式的表示法，使用文本表示Javascript对象的信息，***本质是一个字符串***。

```javascript
var obj = {a:"hello",b:"World"};//这是一个对象
var json = '{"a":"hello","b":"World"}';//这是一个JSON字符串，本质是一个字符串
```

21世纪初，Douglas Crockford 寻找一种简便的**数据交换格式**，能够在服务器之间交换数据。当时通用的数据交换语言是 XML，但是 Douglas Crockford 觉得 XML 的生成和解析都太麻烦，所以他提出了一种简化格式，也就是**JSON**。
 JSON 的规格非常简单，只用一个页面几百个字就能说清楚，而且 Douglas Crockford 声称**这个规格永远不必升级，因为该规定的都规定了**。

![1555216364944](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555216364944.png)***JavaScript 对象表示法***
***是轻量级的文本数据交换格式***
 ***更小、更快，更易解析***
***是一种数据格式，不是编程语言***
 虽然具有相同的语法形式，但 JSON 并不从属于 JavaScript
 并不是只有 JavaScript 才使用 JSON，JSON 只是一种数据格式
 很多编程语言都有针对 JSON 的解析器和序列化器



**JSON语法**

并列的数据之间用逗号，分隔；

并列数据的集合（数组）用方括号[]表示；

***字符串必须交双引号***

映射用冒号：表示；

映射的集合（对象）用大括号{}表示



**JSON语法可以表示以下三种类型的值**

简单值：与JavaScript语法相同，可以在JSON中表示字符串，数值，布尔值和null，JSON***不支持***JavaScript中的特殊值***undefined***；

对象：一种复杂数据类型，表示一组**无序**的键值对，键值对中的值可以是任意类型----简单值，对象或数组；

数组：一种复杂数据类型，表示一组**有序**的值的列表，数组的值可以是任意类型----简单值，对象或数组。

**JSON静态方法**

***JSON.stringify(object[,replacer[,space]])方法***

----把JavaScript对象格式转化为JSON字符串

----undefined值会被忽略

----object指定转换对象

----replacer参数过滤器为数组时，结果只包含数组中列出的属性；为函数时，需接受两个参数，属性键名和属性值

----space参数为数值时，表示每个级别缩进的空格数；为字符串时，使用字符串作为缩进字符



***JSON.parse(json[,reviver])方法***

----把JSON字符串解析为原生Javascript对象

----json参数必须是有效的JSON否则会报错

----reviver参数过滤器为函数时需接受两个参数，属性键名和属性值



**JSON原型链**

![1555217766293](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555217766293.png)



**JSON应用**

![1555217820982](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555217820982.png)

```JavaScript
<body>
    <div class="table-responsive container">
        <table class="table table-bordered  table-hover" id="table">
            <tr>
                <th class="col-md-1">序号</th>
                <th class="col-md-1">题目</th>
                <th class="col-md-3">内容</th>
                <th class="col-md-1">作者</th>
            </tr>
        </table>
    </div>
    <script src="data.js"></script>
    <script>
        var table = document.getElementById('table');
        jsonData = JSON.parse(data);
        console.log(jsonData);


        for (var i = 0; i < jsonData.length; i++) {
            var tr = table.insertRow();

            td = tr.insertCell();
            td.innerHTML = i+1;

            td = tr.insertCell();
            td.innerHTML = jsonData[i].title;

            td = tr.insertCell();
            td.innerHTML = jsonData[i].content.replace(/\|/g, "<br/>");
            
            td = tr.insertCell();
            td.innerHTML = jsonData[i].authors;
        }


    </script>
</body>
```

**Table 对象 **
 在 HTML 文档中 <table> 标签每出现一次，一个 Table 对象就会被创建
 var table = document.createElement( "table" )
 常用属性和方法
 table.rows	 —— 返回包含表格中所有 tr 元素的集合
 table.createCaption() —— 为表格创建一个 caption 元素
 table.insertRow(index) —— 在表格中的指定位置插入一个空的 tr 元素
 table.deleteRow(index) —— 从表格删除指定位置的行

**TableRow 对象**
 在 HTML 文档中出现一个 <tr> 标签，就会创建一个 TableRow 对象
 var tr = table.insertRow() 
 常用属性和方法
 tr.cells —— 返回表格行中所有 td 或 th 元素的集合 
 tr.insertCell(index) —— 在一行的指定位置插入一个空的 td 元素
 tr.deleteCell(index) —— 删除表格行中的指定 td 元素

**TableCell 对象**
 在 HTML 文档中出现一个 <td> 标签，就会创建一个 TableCell 对象
 var td = tr.insertCell() 
**TableHeader 对象**
 在 HTML 文档中出现一个 <th> 标签，就会创建一个 TableHeader 对象 
 var th = document.createElement("th"); 





**Ajax**

**HTTP协议**：Web使用一种名为HTTP（HyperText  Transfer  Protocol，超文本传输协议）的协议作为规范，完成从客户端到服务器端等一系列运作流程。而协议是指规则的约定。可以说，Web是建立在HTTP协议上通信的。HTTP 是一种不保存状态，即无状态（stateless）协议。HTTP 协议自身不对请求和响应之间的通信状态进行保存。也就是说在 HTTP 这个级别，协议对于发送过的请求或响应都不做持久化处理。

**URL**（Uniform ResourceIdentifier）

----统一资源标识符

----格式![1555218353229](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555218353229.png)

![1555218361996](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555218361996.png)



**请求响应**

HTTP协议规定，请求从客户端发出，最后服务器端响应该请求并返回

**请求报文**

是由请求方法，请求URL，协议版本可选的请求首部字段和内容实体构成的

**响应报文**

响应报文基本上由协议版本、状态码（表示请求成功或失败的数字代码）、用以解释状态码的原因短语、可选的响应首部字段以及实体主体构成

**方法**（Method  告知服务器意图的HTTP方法）

----GET获取资源

----POST传输实体主体

----PUT传输文件

----DELETE删除文件

----HEAD获得报文首部

----OPTIONS询问支持的方法

指定请求的资源按期望产生某种行为，使用方法下达命令

**状态码**

HTTP 状态码负责表示客户端 HTTP 请求的返回结果、标记服务器端的处理是否正常、通知出现的错误等工作。

![1555218747292](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555218747292.png)

| 状态码 | 原因短语              |
| ------ | --------------------- |
| 200    | OK                    |
| 301    | Moved Permanently     |
| 403    | Forbidden             |
| 404    | Not Found             |
| 500    | Internal Server Error |

**Ajax异步请求**

Ajax（Asynchronous Javascript And XML）
 Ajax 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新
 Ajax 技术与数据格式无关

**XMLHttpRequest**

Ajax 是一种用来改善用户体验的技术，其实质就是使用XMLHttpRequest 对象异步的向服务器发送请求。
 步骤

***----创建XMLHTTP Request对象实例***

new  XMLHttpRequest();

***----创建请求***

open(method,url,bool)method请求类型get/post，url请求地址，bool异步/同步请求true异步



***----发送请求***

send（）内部传递提交参数（POST），没有填null

若要提交数据，也可在 open 方法的 "URL" 后面追加
如：xhr.open('GET','xx.php?name=value&name=value',true)
 请求发送到服务器端，收到数据会自动填充 XHR 对象的属性
 readyState：请求状态
 status：服务器返回的 http 请求响应值
 responseText：服务器返回的文本数据

***----回调事件处理函数***

onreadystatechange：请求状态改变触发器

![1555219403371](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555219403371.png)

readyState为0尚未初始化；为1正在发送请求；为2请求完成；为3请求成功正在接受数据；为4接收数据成功

![1555219580253](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555219580253.png)

**setRequestHeader() 指定请求的 HTTP 头信息**
 xhr.setRequestHeader("Content-Type","application/-www-form-urlencoded");
 POST 请求发送表单数据，把表单数据转换成一个字串

**XMLHttpRequest 对象的属性**
 ----readyState
---- status
---- responseText
 ----onreadystatechange
**XMLHttpRequest 对象的方法**
 ----open( )
 ----setRequestHeader()
 ----send()

**Ajax--get异步请求**

![1555219648537](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\1555219648537.png)

**Ajax--post异步请求**

```JavaScript
var xhr;	
if(window.XMLHttpRequest){
    xhr=new XMLHttpRequest();
}else{
    xhr=new ActiveXObjext('Microsoft.XMLHttp');
}
xhr.open('post' , 'xx.json' , true);
xhr.setRequestHeader("Content-Type","application/-www-form-urlencoded");
xhr.send(null);
xhr.onreadystatechange=function(){
    if(xhr.readyState == 4 && xhr.status == 200){
	   var txt = xhr.responseText;
              document.write(txt);
	       //DOM操作
	}

```

**$.ajax()方法**

该方法是JQuery底层AJAX实现

```JavaScript
$.ajax({
        type: "get",//请求方式
        url: '',//请求地址
        dataType: 'json',//指定数据类型
        success: function (data) {//数据返回成功执行函数
            console.log(data)
        }
    })

```

**$.post( )**post 请求

```JavaScript
$.post(url,
       function (data) {//数据返回成功执行函数
            console.log(data)
       }
)

```

 **$.get( )**get 请求

```JavaScript
$.get(url,
       function (data) {//数据返回成功执行函数
            console.log(data)
       }
)

```





****
 **$.getJSON()** 加载 json 文件

```JavaScript
$.getJSON(url,
       function (data) {//数据返回成功执行函数
            console.log(data)
       }
)

```

