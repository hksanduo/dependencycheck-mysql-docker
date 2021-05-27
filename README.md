# dependencycheck-mysql-docker
## 背景
owasp官方提供了一个dependency check mysql 容器，但是受限于国内网络环境等因素，不怎么好用，这里单独开一个源供自己研究和学习使用。

## 构建
### 标准构建
```
docker build -t dependencycheck-mysql:v1 .
```
### 代理模式
由于dependency check 会更新cve,cpe库，国内网络环境有点儿尴尬，通过配置镜像站，架设代理来解决，使用的是polipo。配置文件如下：
```
logSyslog = true
logFile = /var/log/polipo/polipo.log
socksParentProxy = "192.168.3.254:6666"
socksProxyType = socks5
proxyPort = 8183
proxyAddress = "0.0.0.0"
allowedClients = 127.0.0.1
```

## 运行
```
docker run -d \
--name dc \
-p 3306:3306 \
-it dependencycheck-mysql:v1
```


## 参考
- [https://github.com/stefanneuhaus/dependencycheck-central-mysql-docker](https://github.com/stefanneuhaus/dependencycheck-central-mysql-docker)
