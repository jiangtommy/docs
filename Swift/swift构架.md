#### swift float也可以使用`%`.  
```
let d = 5.2, e = 1.7
d / e  // 3.059
d % e  // 0.1
```
#### Nil Coalescing Operator
```
a ?? b => a != nil ? a! : b
```
e.g.

```
var userNickName:String?
let outputName:String = userNickName ?? "Guest"
print ("Hello, " + outputName)  // "Hello, Guest"

var userNickName:String? = Tommy
let outputName:String = userNickName ?? "Guest"
print ("Hello, " + outputName)  // "Hello, Tommy"
```