## 类型、值和变量
字符串不可变，可以访问字符串任意位置的文本，但是JavaScript并未提供修改已知字符串的文本内容的方法。`replace()`, `toUpperCase()`等都返回新字符串   
变量无类型，可以被赋予任何值。  
不区分整数和浮点数，所有数字均用浮点数表示。   
能识别十进制和十六进制(前缀为`0x`或者`0X`，后跟十六进制数串)，ECMAScript标准不支持八进制，但是某些JavaScript实现可能支持。尽量不使用   
`Infinity`和`-Infinity`，`0`和`-0`,`NaN`   

```
Number.Max_VALUE + 1 = 1/0 = Number.POSITIVE_INFINITY = Infinity
Number.NEGATIVE_INFINITY = -Infinity = -1/0 = -Number.MAX_VALUE - 1
NaN = Number.NaN = 0/0 
Number.MIN_VALUE / 2 
- Number.MIN_VALUE / 2 = -0
```

`NaN`和任何值都不相等，无法通过`x=NaN`来判断`x`是否为`NaN`，可以使用`x!=x`或者函数`isNaN'`来判断。   

```
0 === -0 // true
1/0 === 1/-0 // false Infinity != -Infinity
```
字符串可用`+`直接连接
***
#### null和undefined区别
##### null
`null`是关键字   
表示一个特殊值。  
`typeof(null)   //=> 'object'`.  即：可以将`null`认为是一个特殊的对象值，含义为“非对象”。  
但实际上，通常认为`null`是它自有类型的唯一一个成员，可以表示数字、字符串和对象是“无值”的   

##### undefined
`undefined` 是预定义的全局变量，不是关键字，它的值就是未定义   
是变量的一种取值，表明变量没有初始化。   
`typeof(undefined).   //=> 'undefined'`.   
对象属性或者数组元素不存在时，查询返回`undefined`    
如果函数没有任何返回值， 则返回`undefined`  
引用没有实参的函数形参也会只会得到`undefined`
 ***
#### 包装对象
JavaScript对象是一种复合值，是属性或已命名值的集合。通过"."富豪来引用属性值。   
字符串和数字、布尔值都可以调用属性和方法。   
下面以字符串为例:   

```
var s = "Hello World";
console.log(s.length);      // => 11
```
可以理解为：   
只要饮用了字符串s的属性，JavaScript就会讲字符串通过调用`new String(s)`的方式转换为对象，这个对象继承了字符串的方法。并被用来处理属性的引用。一旦属性引用结束，这个新创建的对象就会被销毁。 (实际上并不一定如此处理，但是可以这么理解)。  

```
var s = "test";        // create a String
s.len = 4;             // set s.len = 4
var t = s.len;         // => undefined
```
如上代码中，第二行创建了一个临时字符串对象，并给其len属性复制为4，随即销毁这个对象。   
第三行通过原始的(未被修改)字符串值创建一个新字符串对象。 并尝试读取len属性，自然不存在。结果为undefined。  
这段代码说明了在读区字符串、数字、布尔值的属性值时，表现的和对象一样。但是如果试图给其属性赋值，则该操作会被忽略。修改只发生在临时对象上，而这个临时对象并为继续保留下来。   
***
原始值(undefined, null, 布尔值，数字，字符串)不可更改，比较时是值的比较。内容相同即可。
对象的比较时引用的比较。两个对象即使包含相同属性和相同值，两个对象也不等。

```
x + ""          //等价于String(x)
+x = x - 0      //等价于Number(x)
!!x             //等价于Boolean(x)
```
***
将数字转换为字符串方法如下：

```
toString()          // 可选参数为转换基数，默认为10进制
toFixed()           //根据小数点后指定位数降数字转换为字符串
toExponential()     // 使用指数记数法，小数点前1位，小数点后位数由参数决定
toPrecision()       //根据指定有效位数，将数字转换为字符串
var n = 123456.789
n.toFixed(0);          // "123457"
n.toFixed(2);          //"123456.79"
n.toFixed(5);          // "123456.78900"
n.toExponential(1);    //"1.2e+5"
n.toExponential(3);    //"1.235e+5"
n.toPrecision(4);.     //"1.235e+5"
n.toPrecision(7);.     //"123456.8"
n.toPrecision(10);.    //"123456.7890"
```
***
JavaScript没有块级作用域。  
JavaScript函数作用域是指在函数哪申明的所有变量，在函数体内都是可见的。 
申明提前(hoisting) JavaScript函数里声明的所有变量(但不涉及赋值)

```
var score = "global";
function f() {
    console.log(scope).  // 输出undefined，而不是global
    var scope = "local";
    console.log("local");
    console.log("scope");
}
```