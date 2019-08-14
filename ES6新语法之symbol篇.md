### 1.基础概念

​		ES5中的对象名都是字符串，这样容易造成属性名的冲突，尤其是使用var来兼容低版本时，所以，为啦引入一种每个属性名都是独一无二的机制，Symbol在ES6中开始引入。

​		symbol是一种新的原始数据类型，表示一种独一无二的值。它是JavaScript语言的第七种数据类型，前六种是：null，undefined，number，string，Boolean，object。

### 2.声明方式

​		symbol值是通过symbol函数生成的。凡是symbol类型的的数据，都是独一无二的，

```	JavaScript
let s = Symbol();
typeof s
// "symbol"
```

​		**注意：**symbol函数前不能使用new命令，否则会报错，这是因为生成的symbol是一个原始的数据类型的值，不是对象。也就是说，由于symbol值不是对象，所以不能添加属性，基本上，他是一种类似于字符串的数据类型。

​		此外，symbol函数可以接受一个字符串作为参数，表示对symbol实例的描述，主要是为啦在控制台显示，或者转为字符串时，比较好区分。

```javascript
let a = Symbol（'foo'）
let b = Symbol ('bar')
a  // Symbol（foo）
b  // Symbol (bar)
a.toString()  //  'Symbol（foo)'
b.toString()  //  'Symbol（bar)'
```

​		如上面代码，有了参数之后，可以更容易的区分两个值，相当于为他们添加上描述。值得注意的时，symbol函数的参数只是表示对当前symbol值得描述，因此，相同参数的symbol函数的返回值是不相等的。

```javascript
let a = Symbol（'foo'）
let b = Symbol ('f00')
a === b // false
```

