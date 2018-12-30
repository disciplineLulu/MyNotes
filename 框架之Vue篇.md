## Vue的基本介绍

### Vue的基本概念

​	他是一个渐进式的JavaScript框架    开发者是尤雨溪（大佬啊，你的3.0出的慢点啊T.T）

### 库和框架的区别

#### 	库：

​		库是一系列的方法的集合，例如jQuery、zepto等等

#### 	框架：

​		框架是一套完整的解决方案。学过的框架有：bootstrap 、mui、 Vue啊其他的还有angular/react等等

#### 	二者的区别：

​		我们写代码时，主动的调用库中的方法，逻辑需要自己控制。而框架是调用我们写的代码，主体逻辑框架控制，一个框架之中可以有很多个库。

#### Vue是一个MVVM框架

​	mvc：后端

​		M： Model			V ：views    			c : controller

![](E:\璐璐的东西不要动\璐璐的笔记\img\mvc.jpg)

​	MVVM：

​		M： Model			V ：view			VM :viewModel   ,  	

​			VM :viewModel	双向数据绑定

​				如果model数据变量，视图（view）自动变化

​				如果视图（view）发生啦改变，数据也发生改变

![](E:\璐璐的东西不要动\璐璐的笔记\img\MVVM.png)



### Vue的基本使用

​	三个步骤

​		1.引入Vue.js文件

​		2.创建一个vue实例

```
const vm = new Vue({
    el:'#id',
    data:{
        msg:'啊  又要放学啦'
    }
});
```

​		3.在页面中使用vue的数据{{msg}}

### Vue的插值表达式

​	{{}}：mustache语法，用于显示data中的数据

​		1.可以直接访问data的数据

​		2.可以出现一个表达式

​		3.不能访问data中不能出现的数据，不能出现语句（js的关键字）

## vue指令集合

### v-bind指令

​	作用：在标签的属性中使用data中的数据（表达式）因为在标签的属性中不能出现{{}}插值表达式

​	缩写：v-bind非常非常实用，可以把v-bind：title  缩写成：title

### v-model指令

​	作用：给表单元素添加，实现双向的数据绑定

​		解释：表单的value的值发生啦改变，数据自动发生改变，数据发生啦改变，表单的value值也会发生改变

​		注意点：一个表单元素，只要用啦v-model，value值就可以不用考虑啦

​	v-model在其他表单的使用：textarea，input ，select

双向数据绑定原理

​	view到model  ：  通过监听DOM的事件，view变啦，修改啦model的数据

​	model到view :	    数据劫持(Object.defineProperty)下的get和set

### v-on指令

​	v-on作用：给元素注册事件

​	语法：v-on：事件名称="事件函数";@事件名称="事件函数";

​	methods:	   给vue提供方法

​				字符串翻转	跑马灯

#### v-on传参问题

​		@事件名称=“事件函数名”  优点：简单，缺点：没法传参，有一个默认参数，就是事件对象

​		@事件名=“事件函数名（）”优点：可以传参  缺点：事件对象不是默认参数，如果想要获取事件对象，手动$event

#### 事件修饰符

​		.prevent     	阻止标签的默认行为

​		.stop		阻止冒泡	

​		.once		只触发一次回调

​		.self			只当事件是从侦听器绑定的元素本身触发时才触发回调

​		.capture		添加事件侦听器时使用capture

​		.passive		以{passive：true}模式添加侦听器

### v-text与v-html

#### v-text

​	用于设置标签的innerText属性，标签不会生效。如果想要修改部分的内容，需要使用插值表达式

#### v-html

​	用设置标签的innerHTML属性，标签能够生效，不安全。

### v-if与v-show

​	作用：都用于控制元素的显示和隐藏

#### v-if

​	通过创建和删除元素来控制

#### v-show

​	通过样式的display来控制显示和隐藏

#### 使用场景

​	对于需要频繁切换显示和隐藏的标签，应该使用v-show，若，要么显示要么隐藏，应该用v-if

### v-else和v-else-if

#### v-else

​	经跟在v-if或者v-else-if后边

#### v-else-if

​	紧跟在v-if或者v-else-if后边

### v-for

​	作用：遍历一个数组或者一个对象

​	如何使用：需要重复渲染谁就给谁加

​	

```
<li v-cloak v-for="item in list" :key="item.id" :class="{completed:item.completed,editing:item.id === temp}" @dblclick="upData(item.id)">
			<div class="view">
				<input class="toggle" type="checkbox" v-model="item.completed">
				<label>{{item.value}}</label>
			<button @click="delData(item.id)" class="destroy"></button>
		</div>
	<input class="edit" v-model="item.value" @keyup.enter="changeData">
</li>
```

#### key属性的作用

​	只要用啦v-for，都应该指定一个唯一的key属性

### v-cloak

​	解决插值表达式闪烁的问题

### v-pre

​	元素 跳过这个元素  不渲染

### v-once 

​	只渲染一次，后续数据更新不会重新渲染



## vue的选项/数据

### 	data属性

​	vue的数据实例对象，基本上所有的属性都放在date中

```

<li v-for="item in list">
	<label>{{item.value}}</label>
</li>

data: {
	list: [],
	addData: '',
	temp: -1
 }
```



### 	methods属性

​	vue的方法实例对象，可以直接通过vm实例访问这些方法。

```
vue的方法属性之中有两种方法，一种传参，一种不传参
1.传参
<input  @keyup.enter="addDate" >
2.不穿惨
<button @click="delData(item.id)" class="destroy"></button>
		
methods: {
			addDate() {
				this.list.unshift({
					value: this.addData,
					id: new Date().getTime(),
					completed: false
				})
				this.addData = ''
			},
			delData(id) {
				let index = this.list.findIndex(item => item.id === id)
				this.list.splice(index, 1)
			}
		}
```



### 	computed属性

​	vue的计算属性的方法，不建议写箭头函数

​	

```
computed:{
			all(){
				return this.list.length  > 0
			},
			success(){
				return this.list.filter( v => !v.completed ).length
			},
			other(){
				return this.list.some( v => v.completed )
			}
		},
```



### 	watch属性

​	vue的数据监察属性，一旦监视的属性发生变化，就会触发这个时间中的方法

​	

```
不加deep时是监听简单数据类型的
watch:{
			list:{
				handler:function(value){
					console.log('666')
					localStorage.setItem('todo',JSON.stringify(value))
				},
				deep:true
			}
```

## vue的生命周期

​	生命周期：一个事物从出现到消亡的整个过程

​	vue的生命周期：一个vue实例从创建到最后销毁的整个阶段

### 	vue的钩子函数

#### 	1.beforeCreate

​	在vue实例化初始前调用	

#### 	2.created

​	在实例创建完成后立即调用

​	3.beforeMount

​	在挂载到具体的标签之前调用

​	4.Mounted

​	el被新创建的vm.$el替代，并挂在到实例上之后调用该钩子

​	5.beforeUpdate

​	数据更新时调用，发生在虚拟dom打补丁之前

​	6.updated

​	由于数据更改导致的虚拟dom重新渲染和打补丁，在这之后会调用该钩子

​	7.activated

​	keep-alive 组件激活时调用。

​	8.deactivated

keep-alive 组件停用时调用。

​	9.beforeDestroy

​	实例销毁之前调用，在这一步实例仍然完全可用。

​	10.destroyed

​	vue实例销毁后调用

​	11.errorCaptured

​	错误传播规则。2.5.0新增

​	







#### 



​		

