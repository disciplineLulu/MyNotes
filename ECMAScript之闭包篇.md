## 闭包的概念

​	闭包是函数和声明该函数的词法环境的组合
​	闭包中包含啦内部函数的代码,以及所需的外部函数中的变量引用

## 闭包产生的条件

​	当内部函数被保存到啦外部时,就会形成闭包

## 闭包的作用

​	1.变量私有化,保护数据安全
​	2.持久化维持数据

## 闭包存在的问题

​	闭包占用的内存是不会释放的,因此,如果滥用闭包,就会造成内存泄漏.闭包很强大,但是也只是在必须使用的时候使用闭包

## js的垃圾回收机制

​	https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Memory_Management