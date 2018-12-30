## CSS背景(background)

### 背景颜色

background-color背景颜色

### 背景图片

background-image:url("")  背景图片
​			url后的括号内一定要加双引号

### 背景对齐方式

background-repeat  背景图片的对齐方式
​		有四个值  

1. repeat横向和纵向平铺  
2. no-repeat背景图片不平铺 
3. repeat-x背景图片横向平铺 
4. repeat-y背景图片纵向平铺

### 背景图片的位置

background-position背景图片的位置
​			其中N为横向  F为纵向   可以填写像素,百分比还可以填写left等固定值

### 背景附着

background-attachment背景附着
​			1.scroll  背景图片随滚动条一起滚动
​			2.fixed  背景图片不动

### 背景透明

background-color:rgba();

详情参照上方css外观文本颜色处介绍关于颜色的介绍

### 精灵图技术

​			就是imaage+position+repeat控制效果



## CSS3背景

在CSS2中已经有啦背景系列的样式,在CSS3中又新增啦几个属性

### background-size

​	用于设置背景图片的大小，可以跟具体的数值   比如:600px   800px

​	也有特殊值	contain	保证等比例缩放,但是会出现留白

​				cover也会等比例缩放,并且不会出现留白,只是会有一部分图片不显示

### background-clip

​	设置背景图片的区域大小

- ​		border-box   背景区域包括啦边框
- ​		padding-box   背景区域只包括内容和padding
- ​		content-box    背景区域只有content部分

### background-origin

​     设置背景图片的原点位置(就是从哪里开始铺),用的多的是用于放大或者缩小时候的中心定位

- ​	padding-box   默认值,从外边距开始
- ​	border-box   从边框开始
- ​	content-box   从内容开始

### 多重背景

个背景之间用逗号隔开例如background: url(images/mn1.jpg) no-repeat top left, url("images/mn2.jpg") no-repeat right bottom, pink;