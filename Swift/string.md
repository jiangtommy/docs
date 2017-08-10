#### 空字符串
两种方式创建空字符串，可以用isEmpty查看字符串是否为空。

```swift
var s1 = ""  //method 1
var s2 = String()  //method 2
s1.isEmpty // true
s2.isEmpty // true
```

#### 字符串拼接
字符串之间拼接可以直接使用`+`，但是字符串和`Character`之间不能使用`+`进行拼接，可以使用`append`添加到最末端。 

```
var str1:String = "hello world"
var ch:Character = "!"
var str2:String = "!"
str1 += ch  //报错
str1.append(ch) // "hello world!"
str1 += str2  // "hello world!!"
```
#### 字符串长度
在`Objective-C`中通常使用`length`来获取`NSString`类型的字符串长度，但是在`Swift`中，`String`结构中没有这个方法，可以使用`String`的扩展属性成员`characters`的`count`属性来获取。 

```
var strObjC:NSString = "hello world"
strObjC.length // 11
var strSwift:String = "hello world"
strSwift.characters.count // 11
```
#### 字符串插值 String Interpolation
`\(other Type)`

#### 前后缀 Prefix and Suffix
`.hasPrefix` and `.hasSuffix`    
`str1.hasPrefix(str2)`   
`str1.hasSuffix(str2)`

#### trim
```Swift
var s6 = "     !hi!!!!     "
s6.trimmingCharacters(in: CharacterSet.whitespaces) // "!hi!!!!"
s6.trimmingCharacters(in: CharacterSet.init(charactersIn: " !")) // "hi"
```

#### split
```Swift
var s7 = "welcome to play swift"
s7.components(separatedBy: " ") //["welcome", "to", "play", "swift"]
```

#### join
