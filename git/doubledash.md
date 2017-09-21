##double dash
`--`(double dash) 是bash的内置命令，用来标记可选命令选项的结束。在它后面带`--`的字符串，不被当做是一个命令选项。
> More precisely, a double dash (--) is used in bash built-in commands and many other commands to signify the end of command options, after which only positional parameters are accepted.

For example:
在`grep`命令中，`-V`原本是一个可选命令参数(options)，打印出`grep`的版本。
```bash
grep -V // check grep version
grep -- -V readme.txt // find '-V' in readme.txt
```
Git 的一些命令中，借鉴了这种用法。使用 -- 去隔离开“树”与“路径”。   
你想还原 一个文件 path/to/file.txt，在Git中使用如下命令   
`git checkout path/to/file.txt`   
但是天杀的居然有一个文件名字就叫做 "master"   
如果你套用上面的命令，想还原“master”文件   
`git checkout master`   
最终起的效果是变成切换到了master分支上。   
正确的做法是使用`--`，这样它后面的字符串不会当做“树”，而认为是文件路径。   
`git checkout -- master`