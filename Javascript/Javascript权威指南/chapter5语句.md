## 语句
JavaScript中没有块级作用域，在语句中申明的变量并不是语句块私有的（**ES6中有块级作用域使用let申明变量**）   
`var`申明的变量无法通过`delete`来删除 

---  
`for/in`语句：

```Javascript
for (variable in object)
	statement
```
**Note:** 只要`for/in`循环中`variable`的值可以党组赋值表达式的左值，它可以时任意表达式。每次循环都会计算这个表达式，也就是说每次循环它计算的值有可能不同。e.g. 可以使用如下代码将所有对象属性复制至一个数组中：

```Javascript
	var o = {x:1, y:2, z:3};
	var a = [], i = 0;
	for (a[i++] in o) /* empty */;
```
`for/in`循环只遍历可枚举的属性。   
ECMAScript规范并没有制定`for/in`循环按照何种顺序来枚举对象属性，实际上，主流浏览器厂商的JavaScript实现时按照属性定义的先后顺序来枚举简单对象的属性，先定义的属性先枚举。

---
#### with 语句
`with`语句用于临时扩展作用域链，用法如下：

```Javascript
	with (object)
	statement
```
这条语句将object添加到作用域链的头部，然后执行statement，最后把作用域链恢复到原始状态   
**Notes:**严格模式中，`with`语句被禁止使用。在非严格模式里也不推荐使用。（难于优化)    
**Notes:**`with`语句提供了一种读取o的属性的快捷方式，但是并不能创建o的属性。如下`with (o) x = 1;`如果`o`包含属性`x`，该属性值被赋值为1，如果`o`不包含`x`，则不会创建`o.x`，而是和没有`with(o)`相同，创建一个局部或者全局变量`x`并赋值为1.   
