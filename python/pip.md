#### proxy
1. check if configure file exists or not, if not, create it.

- Unix: $HOME/.config/pip/pip.conf
- Mac: $HOME/Library/Application Support/pip/pip.conf
- Windows：%APPDATA%\pip\pip.ini %APPDATA%的实际路径我电脑上是C:\Users\user_xxx\AppData\Roaming，可在cmd里执行echo %APPDATA%命令查看

content:   
```
[global]
index-url = http://mirrors.aliyun.com/pypi/simple/ # 这里使用的是阿里云的镜像源
proxy=http://xxx.xxx.xxx.xxx:8080 # 替换出自己的代理地址，格式为[user:passwd@]proxy.server:port

[install]
trusted-host=mirrors.aliyun.com # 信任阿里云的镜像源，否则会有警告
```

[link](https://pip.pypa.io/en/stable/user_guide/#config-file)