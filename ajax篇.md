Ajax

### Ajax是什么

​	1.Asynchronous   JavaScript  and  XML ，AJAX不是一门的新的语言，而是对现有技术的综合利用，本质是在HTTP协议的基础上以异步的方式与服务器进行通信。

​	2.异步：某段程序执行时不会阻塞其他程序的执行，表现形式时程序的执行顺序不依赖程序本身的书写顺序，相反的情况依次执行，那就是同步。核心在于不会阻塞程序的执行，从而提高整体执行效率

### 原生Ajax的使用

#### XMLHttpRequest

- XMLHttpRequest是浏览器的内置对象，作用是在后台与服务器通信（交换数据）
- 用于网页的局部更新，而不是刷新整个页面

```
创建一个新的XMLHttpRequest对象
var  xhr  = new XMLHttpRequest();
```

#### 请求Request

Http请求由3个部分组成，正好和XMLHttp相对应

##### 1.请求行  open

```
xhr.open(请求方式，请求地址，是否同步)
```

##### 2.请求头  setRequestHeader

```
//post请求需要设置请求头
xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoed');
//get请求可以不用设置请球头
```

##### 3.请求主体   send

```
xhr.send('name=lihe&age=64');
//get可以传空
```

##### 响应Response

1.HTTP响应是由服务端放出的，客户端更应该关心的是响应端的结果。

2.HTTP响应由三个部分组成，与XMLHttpRequest的方法或属性成对应关心。

3.由于服务器做出响应需要时间（网络延迟等原因），所以需要监听服务器响应关心，在进行处理

```
if(xhr.readyState == 4 && xhr.status == 200){
    获取数据后进行下一步操作
    var info = xhr.responseText;
}
```

#### 步骤分析

1.请求未初始化（还没有调用open（））

2.请求已经建立，但还是没有发送（还没有调用send（））

3.请求已发送，正在处理中（通常现在可以从响应中获取内容头）

4.请求在处理中，通常响应中已经有部分数据可以用啦，但是服务器还没有完全完成响应

5.响应已经完成，可以获取并使用服务器的响应的数据啦

#### 其他注意点

1.可以使用onreadystatechange来监听XMLHttpRequest的状态

2.获取行状态（包括行状态码和状态信息）

```
xhr.status   //状态码
xhr.statusText  //状态信息
```

3.获取响应头

```
 xhr.getResponseHeader( 'Content-Type' );
 xhr.getAllResponseHeaders();
```

4.获取响应主体

```
xhr.responseText     //json，文本类型
xhr.responseXML		//XML类型
```

### API详解

1.xhr.open()   发送请求，可以使get或者post方式

2.xhr.setRequestHeader()  设置请求头

3.xhr.send()   发送请求主体，如果是get方式使用xhr.send(null),因为get方式在open中已经发送啦请求主体

4.xhr.onreadystatechange = function(){ }    监听响应状态

5.xhr.status  表示响应码，如200表示成功

6.xhr。statusText  表示响应信息。如ok

7.xhr.getAllResponseHeaders() 获取全部响应头信息

8.xhr.getResponseHeader('key')  获取指定响应头信息

9.xhr.reponseText  xhr.responseXML  都表示响应主体，返回的数据格式不同

### get和post的差异

1.get没有请求主体，使用xhr.send(null)发送请求主体，它的数据在open中发送
2.get课以通过请求URL上添加请求函数

3.post可以设置xhr.send('name=it&age=64')发送请求主体

4.post需要设置

5.get性能高（基本上获取内容都是使用get）

6.get大小限制4kb   post则没有限制

#### get方式的请求响应

```
const xhr = new XMLHttpRequest;
	xhr.open('get','mmp.data');
	xhr.send(null);
	xhr.onreadystatechange = function(){
        if(xhr.status == 200 && xhr.readyState == 4){
            //获取到XML格式内容   返回的是DOM对象
            var xml = xhr.responseXML;
            //通过选择器可以获取到XML的数据
             console.log(xml.querySelectorAll('array')[0].querySelector('src').innerHTML);
        }
	}
```

#### post请求和响应

```
初始化
const xhr = new XMLHttpRequest;
请求行
xhr.open('post','data.json');
请求头
xhr.setRequestHeader('content-type','application/x-www-form-urlcoded');
请求内容
xhr.send('name=shadiao&age=64');
监听响应改变
xhr.onreadystatechange = function(){
  /*什么时候才算是http通讯结束 在readyState=4的是 响应完成*/
        /*什么是才算是通讯成  status 200 */
     if(xhr.status ==200 && xhr.readyState == 4){
            document.querySelector("div").innerHTML = xhr.responseText;
        }
}
```

## XML和JSON

### XML

1.XML是可扩展标记语言（Extensib Markup Language）的缩写，其中的标记（markup）是关键部分。XML可以创建内容，然后使用限定标记标记它，从而使每个单词、短语或块成为可识别、可分类的信息。您穿建的文件，或文档实例由元素（标记）和内容构成。

2.特点

- ​	必须有根元素
- ​	不能以空格，数字或者开头大小写敏感
- ​	不能交叉嵌套
- ​	属性双引号
- ​	特殊符号要使用实体
- ​	注释和HTML一样

3.XML虽然可以描述和传输复杂数据，但是其解析过于复杂并且体积较大，所以实际开发是使用较少

4.格式

```
 <?xml version="1.0" encoding="UTF-8"?>
    <root>
    <arrayList>
        <array>
            <src>images/banner.jpg</src>
            <newPirce>12.00</newPirce>
            <oldPrice>30.00</oldPrice>
        </array>
        <array>
            <src>images/banner.jpg</src>
            <newPirce>12.00</newPirce>
            <oldPrice>30.00</oldPrice>
        </array>
    </arrayList>
    </root>
```

### JSON

JavaScript Object Notation ,另一种轻量级的文本数据交换格式，独立于语言。

#### 特点

```
1.数据在键值对中
2.数据有","分隔，最后一个兼职不能带","
3."[]"保存数组，"{}"保存对象
4.使用""双引号包裹键值
```

例如

```
 [
        {"src":"images/detail01.jpg","oldPrice":"10.12","newPrice":"130.00"},
        {"src":"images/detail02.jpg","oldPrice":"1.00","newPrice":"11.00"},
        {"src":"images/detail03.jpg","oldPrice":"100.00","newPrice":"1000.00"}
    ]
```

#### 不同语言下的解析   JSON

##### 1.PHP方法

- json_encode();将PHP数组转化成json字符
- json_decode();将json字符串转换为PHP数组

##### 2.JavaScript解析方法

json对象

​	json.parse();字符串转json对象

​	json.stringify();json对象转字符串

示例：

```
 var xhr = new XMLHttpRequest;
    xhr.open('get','01.php');
    xhr.send(null);
    xhr.onreadystatechange = function(){
       if(xhr.status == 200 && xhr.readyState == 4){
           /*获取仅仅是字符串*/
           var text = xhr.responseText;

           /*需要把字符串转化成JSON对象*/
           var json_obj = JSON.parse(text);
           console.log(json_obj);

           /*我们也可以把JSON对象转化成字符串*/
           var json_str = JSON.stringify(json_obj);
           console.log(json_str);
       }
    }
```

## 封装Ajax工具函数

```
 /*
    * 1. 请求的类型                type    get post
    * 2. 请求地址                  url
    * 3. 是异步的还是同步的         async   false true
    * 4. 请求内容的格式            contentType
    * 5. 传输的数据                data    json对象
    *
    * 6.响应成功处理函数           success   function
    * 7.响应失败的处理函数         error     function
    *
    * 这些都是动态参数  参数对象  options
    * */

    /*封装一个函数*/
    window.$ = {};
    /*申明一个ajax的方法*/
    $.ajax = function(options){

    if(!options || typeof options != 'object'){
        return false;
    }

    /*请求的类型*/
    var type = options.type || 'get';/*默认get*/
    /*请求地址 */
    var url = options.url || location.pathname;/*当前的地址*/
    /*是异步的还是同步的 */
    var async = (options.async === false)?false:true;/*默认异步*/
    /*请求内容的格式 */
    var contentType = options.contentType || "text/html";

    /*传输的数据 */
    var data = options.data || {};/*｛name:'',age:''｝*/
    /*在提交的时候需要转成 name=xjj 这种格式*/

    var dataStr = ''/*数据字符串*/

    for(var key in data){
        dataStr += key+'='+data[key]+'&';
    }

    dataStr = dataStr && dataStr.slice(0,-1);

    /*ajax 编程*/
    var xhr = new XMLHttpRequest();

    /*请求行*/
    /*(type=='get'?url+'?'+dataStr:url)判断当前的请求类型*/
    xhr.open(type,(type=='get'?url+'?'+dataStr:url),async);

    /*请求头*/
    if(type == 'post'){
        xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoded');
    }

    /*请求主体*/
    /*需要判断请求类型*/
    xhr.send(type=='get'?null:dataStr);

    /*监听响应状态的改变  响应状态*/
    xhr.onreadystatechange = function(){
        /*请求响应完成并且成功*/
        if(xhr.readyState == 4 && xhr.status == 200){
            /*success*/
            var data = '';
            var contentType = xhr.getResponseHeader('Content-Type');
            /*如果我们服务器返回的是xml*/
            if(contentType.indexOf('xml') > -1){
                data = xhr.responseXML;
            }
            /*如果我们的服务器返回的是json字符串*/
            else if(contentType.indexOf('json') > -1){
                /*转化json对象*/
                data = JSON.parse(xhr.responseText);
            }
            /*否则的话他就是字符串*/
            else{
                data = xhr.responseText;
            }

            /*回调 成功处理函数*/

            options.success && options.success(data);
        }
        /*计时请求xhr.status不成功  他也需要的响应完成才认作是一个错误的请求*/
        else if(xhr.readyState == 4){
            /*error*/
            options.error && options.error('you request fail !');

        }

    }
    }
    $.post = function(options){
    options.type = 'post';
    $.ajax(options);
    }
    $.get = function(options){
    options.type = 'get';
    $.ajax(options);
    }
```

## jQuery中的Ajax

- jQuery为我们提供啦更强大的Ajax封装
- $.ajax({ })可配置方式发起Ajax请求
- $.get()以get方式发起Ajax请求
- $.post以post方式发起Ajax请求
- $('from').serialize()序列化表单（几个实话key=val&key=val)
- url接口地址
- type请求方式
- timeout请求超时
- datatype服务器返回格式
- data发送请求数据
- beforeSend：function(){ }请求发起前调用
- success 成功响应后调用
- error错误响应时调用
- complete  响应完成时调用
- jQueryAjax介绍

- <http://www.w3school.com.cn/jquery/jquery_ref_ajax.asp>

### jQuery中Ajax的使用

```
$.ajax({
    type:请求方式默认get方式,
    url:请求的地址，
    data：{}请求是传的参数是一个对象，
    datatype：服务器返回参数的类型，
    beforesend：function（）{
    请求发送之前调用
    }，
    success:function(info){
        请求成功是调用
    },
    complete：function(){
        请求完成后调用
    }，
    error：function（）{
    请求失败时调用
    }
})
```

### jQuery中的Ajax

1.url:要求为string类型的参数，（默认为当前页地址）发送请求的地址。

2.type：要求为string类型的参数，请求方式默认为get。注意其他HTTP请求方式，例如put和delete也可以使用，但仅部分浏览器支持。

3.timeout:要求为number类型的参数，设置请求超时时间（毫秒），此设置将覆盖$.ajaxStup()方法的全局设置。

4.async:要求为boolean类型的参数，默认设置为true。所有的请求均为异步请求。如果需要发送同步请求，请将此项设置为false。注意，同步请求将锁住浏览器，用户其他操作必须等待请求完成才可以执行。

5.cache   要求为Boolean类型的参数，默认为true（当dataType为script是，默认为false）。设置为false将不会从浏览器缓存中加载请求信息。

6.data   要求为Object或string类型的参数，发送到服务器的数据。如果已经不是字符串，将自动转化为字符串格式。get请求中将附加在URL后。为防止这种自动转换，可以看processData选项。对象必须是key/value格式。如果是数组，jQuery将自动为不同值对应为同一个名称。

7.datatype  要求为string类型的参数，语气服务器返回的数据类型。如果不指定，jQuery将自动根据HTTP包mime信息返回responseXML或responseText，并作为回调函数传递。

​	可用类型如下：

​		xml：返回XML文档，可用jQuery处理。

​		HTML：返回纯文本HTML信息；包含script标签会在插入dom时执行。

​		script：返回纯文本JavaScript代码。不会自动缓存结果。除非设置cache参数。注意在远程请求是（不在同一个域下），所有post请求都将转换为get请求。

​		json：返回json数据。

​		jsonp：jsonp格式。使用sonp形式调用函数时，例如myurl=？callback=？，jQuery将自动替换后一个"?"为正确的函数名，以执行回调函数。

​		text:返回纯文本字符串。

8.beforeSend：要求为Function类型的参数，发送请求钱可以修改为XMLHttpRequest对象的函数，例如添加自定义HTTP头。在beforeSend中如果返回false可以取消本次Ajax请求。XMLHttpRequest对象是唯一的参数。  

9.success：要求为Function类型的参数，请求成功后调用的回调函数，有两个参数。

1. 由服务器返回，并根据dataType参数进行处理后的数据。
2. 描述状态的字符串。

10.error：要求为Function类型的参数，请求失败时被调用的函数。该函数有3个参数，即XMLHttpRequest对象、错误信息、捕获的错误对象(可选)。

