## object  对象

### 	神马是对象

​		在现实生活中,万物皆对象
​		对象是一个具体的事物,一个具体的事物就会有  特征和行为
​		js中的对象就是生活中对象的一个抽象...没有特征和行为,取而代之的是属性和方法
​		是一个无序的键值对的集合
​		对象用无序的键值对存放一组无序的数组,比如一个人的行为和特征

### 	创建对象

#### 		1.对象字面量

```
var p = {};
var p = {
    name : 'zs',
    age:18,
    sayHi:function(){
        console.log(this.name)
    }
}
```



#### 		2.通过Object构造函数创建

```
var p =  new Object(); // 创建一个空的对象
var p =  new Object({name :'xx'});
```



#### 		3.函数工厂

​			优点:可以同时创建多个对象
​			缺点:创建出来的对象没有具体的类型,都是object类型

```
//例如
定义一个函数，用于创建学生对象
  //工厂函数：
  function createStudent(name, age, sex) {
    //1.创建空对象
    var stu = {};
    //2. 赋值
    stu.name = name;
    stu.age = age;
    stu.sex = sex;
    stu.sayHi = function() {
      console.log("大家好,我是"+this.name);
    }
    //3 . 返回
    return stu;
  }

  var stu1 = createStudent("zs", 18, "男");
  stu1.sayHi();
```



#### 		4.自定义构造函数

​		构造函数是一种特殊的函数,主要用来在创建对象时初始化对象,即为对象成员变量赋初始值,总与new运算符一起使用在创建对象的语句中.

```
//所有创建出来的对象都有：
    //name
    //age
    //hobboy
  function Teacher(name, age) {
    //构造函数内部的this指向的是新创建的那个对象
    this.name = name;
    this.age = age;
  }

  var tea = new Teacher("zs", 18);
  console.log(tea);
```



##### 		注意

​		1.构造函数的首字母要大写
​		2.构造函数要于new一起使用才有意义
​		3.构造函数的作用时用于实例化一个对象,即给对象添加属性和方法

#### 删除对象的属性

​	delete obj.name;//删除obj的name属性

#### 查看一个对象的类型

​		typeof  只能判断基本的数据类型的类型
​		instanceof  判断对象的具体类型
​		constructor.name  也可以获取到对象的具体类型

#### 关于new的执行

​		1.new会创建一个新的对象,类型是object
​		2.new会让this指向这个新的对象
​		3.执行构造函数  目的是为啦给这个新对象加属性和方法
​		4.new会返回这个新对象

#### 对象的遍历

​	使用for...in语法来遍历对象
​		

```
for (var key in obj) {
    //  key是 键 
    console.log(key);
    // 值
    console.log(obj[key]);
}
```

​	判断一个属性是否在这个对象内也用in语法(不常用)
​			

```
if (属性名  in  对象) { .. }
```

​	获取对象内的所有属性(不常用了解即可)
​		

```
// 结构 :   Object.keys(对象)
Object.keys(obj)
```



## javescript的内置对象(方法)

### Math对象

#### 1.π

​	Math.PI()

#### 2.最大值和最小值

​	Math.max()   最大值
​	Math.min()  最小值

#### 3.取整(重要)

​	Math.ceil()   向上取整
​	Math.floor()  向下取整
​	Math.round()  四舍五入

#### 4.随机数(常用)

​	Math.random()   在[0,1)之间取值,始终大于0小于1

#### 5.绝对值

​	Math.abs()  求绝对值

#### 6.求次幂和平方

​	Math.pow(num,power)   求num的power次方
​	Math.sqrt(num)   对num开平方

### Date对象

#### 创建一个日期对象

​	1.var  data = new Date();   //使用构造函数创建一个当前时间的对象
​	2.var  data = new Date("2017-03-02");创建一个指定时间的日期对象
​	3.var  data = new Date('2017-03-02 00:02:34');  创建一个指定时间的日期对象
​	4.var  data = new Date(2017,2,22,0,25,33);  创建一个指定时间的日期对象   
​	5.var  data = new Date(15613554156536);   参数毫秒
​	date构造函数的参数
​		1.毫秒数  	654654653654161651
​		2.日期格式   	2017-03-02
​		3.年日月		2017,2,22,0,25,33

#### 日期格式化

​	date.toLocalString();   本地风格的日期格式
​	date.toLocaleDateString();  获取日期
​	date.toLocaleTimeString();   获取时间

#### 获取日期的指定部分

​	getMilliseconds()    获取毫秒值
​	getSeconds();   获取秒
​	getMinutes()  获取分钟
​	getHours()   获取小时
​	getDay(0  获取星期
​	getDate()   获取日
​	getMonth()   获取月份
​	getFullYear()   返回四位数的年份

#### 时间戳

​	

```
var date = +new Date();//1970年01月01日00时00分00秒起至现在的总毫秒数

// 开始 
var start = +new Date();
for ( var i = 1 ; i <= 1000 ; i++) {

    console.log(i);
}
// 结束
var end = +new Date();

console.log('时间戳 :' + (end-start));
```

### Array对象

#### 1.数组的拼接 arr.join()

```
先声明一个数组
var arr = [1,2,3,4,5];
调用方法即可
arr.join();
```



##### 注意

​	1.join()方法的括号内可传参,   按穿的参数来拼接,  不传参按默认的用逗号进行拼接
​	2.要声明一个变量来接受拼接后的值,join()方法不会改变原数组

#### 2.数组的增删改查

##### 	array.push(元素)

​		在数组的最后位添加一个元素,返回新数组的length

##### 	array.pop()

​		将数组的最后一位删除,返回被删掉的元素

##### 	array.unshift(元素)

​		在数组的最前方添加一位元素,返回新数组的长度

##### 	array.shift()

​		将数组最前面(就是第一个)的元素删掉,返回删除掉的那个元素

#### 3.数组的翻转和排序

​	array.severse()   反转数组
​	array.sort() 	这个方法貌似是按照ASCII表排序的
​	关于ASCLL表在这个网站	https://baike.baidu.com/item/ASCII/309296?fr=aladdin

#### 4.数组的拼接和截取

​	array.concat(array2)  数组合并,但不会影响原数组
​	array.slice(a,b)   数组截取   从第a位开始,到第b位结束  且原数组不会受到影响
​	array.splice(a, b, c)    可以截取也可以添加     

​		从第a位开始,截取第b位,然后在当前位置添加c     如果不穿c   就是只截取不添加

### 基本包装对象

#### Number对象

​	1.toFixed(a);    保留a为小数
​	2.toString()   转换成字符串

#### Boolean对象

​	toString()   转换成字符串

#### String对象

##### 查找指定字符串

​	1.indexof();    获取某个字符串出现的第一个位置,如果没有,返回-1
​	2.lastIndexOf()   获取某个字符传最后一次的位置,如果没有,返回-1

##### 去除空白

​	trim()   去除字符串两边的空白

##### 大小写转化

​	1.toUpperCase();    全部转换成大写字母
​	2.toLowerCase();    全部转换成小写写字母

##### 字符串的截取与拼接

###### 拼接

​	+拼接

###### 截取

​	1.slice	截取出来 从start开始，end结束，并且取不到end
​	2.substring	从start开始，end结束，并且取不到end
​	3.substr		从start开始,截取length个字符
​	优先使用3

##### 字符串切割

​	split
​	与join相反,将字符串分割成数组
​	用法示例

```
//split:将字符串分割成数组
//功能和数组的join正好相反。
var str = "张三,李四,王五";
var arr = str.split(",");
```

##### 字符串替换

​	replace()
​	用法实例

```
replace(searchValue, replaceValue)  //  replace(old, new)
```

​	注意://参数：searchValue:需要替换的值    replaceValue:用来替换的值