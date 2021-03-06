## 对象
属性名可以是包含空格在内的任意字符串，包括保留字，但是一个对象中不能有两个相同名称的属性。   
所有通过对象直接量创建的对象都具有同一个原型对象`Object.prototype`。通过关键字`new`和构造函数调用创建的对象的原型就是构造函数的`prototype`属性值。   
`Object.create()`用来创建新对象，其中第一个参数为这个对象的原型。   
可以通过传入参数`null`来创建一个没有原型的新对象。如果要创建一个普通的空对象，则传入`Object.prototype`。它可以通过任意原型创建新的对象（即可以是任意对象可继承)

---
#### 删除属性
`delete`只是断开属性和宿主对象之间的联系，而不会去操作属性中的属性。e.g.

```
a = {p: {x: 1}};
b = a.p;
delete a.p
b.x  // => 1
```
上述代码中已经删除的属性应用仍然存在。   
`delete`只能删除自由属性，不能删除继承属性。   
`delete`不能删除那些可配置型为false的属性。通过变量声明和函数声明创建的全局对象属性默认不可配置。所以`delete`不能删除`var`定义的全局变量。

---
#### 检测属性
JavaScript对象可以看作是属性的集合。判断属性是否存在于某个对象中，可以使用`in`运算符，`hasOwnProperty（)`和`propertyIsEnumerable()`方法来实现。   
`hasOwnProperty()`方法用来检测给定的名字是否为对象的自由属性，无法检测继承属性。   
`propertyIsEnumberable()`方法是`hasOwnProperty()`的增强版，只有检测到是自由属性且该属性的可枚举性为`true`时才返回`true`。   
`Object.keys()`返回一个数组，这个数组由对象中可枚举的自有属性的名称组成。   
Object.getOwnPropertyNames()`返回对象的所有自有属性的名称。（包括不可枚举的)。 

---
#### 属性的特性
数据属性的4个特性：值（value)、可写性（writeable)、可枚举性（enummerable)和可配置性（configurable)   
存储器属性的4个特性：可读性，可写性，可枚举性和可配置性   
`Object.getOwnPropertyDescriptor()`可获取某个对象特定属性的属性描述符。**Note：**从名字也可以看出，该函数只能获取自有属性的属性描述符。如果想要获取继承属性的特性，需要遍历原型链。   
`Object.definePeoperty()`用来设置属性特性或者新建某种特性的属性。**Note：**只适用于自有属性。   
`Object.defineProperties()`同时创建或者修改多个属性。

###### 属性的规则  
- 如果对象是不可扩展的，则可以编辑已有的自有属性，但是不能给它添加新的属性。
- 如果属性是不可配置的，则不能修改它的可配置性和可枚举性。
- 如果存取器属性是不可配置的，则不能修改其`getter`和`setter`方法，也不能将它转换为数据属性。
- 如果数据属性是不可配置的，则不能将它转换为存取器属性。
- 如果数据属性是不可配置的，则不能将它的可写性从`false`改为`true`，但是可以从`true`改为`false`.
- 如果数据属性是不可配置且不可写的，则不能修改它的值。然而可配置但不可写的属性的值是可以修改的（实际上是先将它标记为可写，然后修改值，最后转换为不可写)

---
#### 对象的属性
每一个对象都有与之相关的三个属性：原型（prototype)、类（class)和可扩展性(extensible attribute)   
###### 类属性
对象的类属性是一个字符串，泳衣表示对象的类型信息。目前只可通过默认的`toString()`方法获取。   
调用对象的`toString()`方法，然后提取返回字符串的**第8个到倒数第二个位置之间的字符**   
由于很多对象继承的`toString()`方法都重写了，所以为了能调用正确的`toString()`方法，需要间接调用`Function.call()`方法。

```Javascript
// 获取类函数方法
function classof(o) {
	if (o === null) return "Null";
	if (o === undefined) return "Undefined";
	return Object.prototype.toString.call(o).slice(8, -1);
}
```
###### 可扩展性
对象的可扩展性用以表示是否可以给对象添加新属性。   
可通过`Object.esExtensible()`来判断 对象是否可扩展。   
可通过`Object.preventExtensions()`将对象转换为不可扩展。   
**Notes：**一旦将对象转换为不可扩展，则无法将其再转换回可扩展。`preventExtensions()`只影响对象本身的可扩展性，如果给一个不可扩展的对象的原型添加属性，这个不可扩展的对象同样会继承这些新的属性。   
`Object.seal()`除了能够将对象设置为不可扩展的，还可以将对象的所有自有属性都设置为不可配置的。不能给该对象添加新属性，而且它的一有属性也不能删除或配置，不过它已有的可写属性依然可以设置。可以通过`isSealed()`来检测对象是否封闭。   
`Object.freeze()`将更严格的锁定对象。`Object.isFrozen()`可用来检测对象是否冻结。

