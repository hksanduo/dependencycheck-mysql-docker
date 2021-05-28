# dependencycheck-mysql-docker
## 背景
owasp官方提供了一个dependency check mysql 容器，但是受限于国内网络环境等因素，不怎么好用，这里单独开一个源供自己研究和学习使用。

## 构建
### 标准构建
```
docker build -t dependencycheck-mysql:v1 .
```
### 代理模式
由于dependency check 会更新cve,cpe库，国内网络环境有点儿尴尬，通过配置镜像站，架设代理来解决。gradle.properties文件中提供两种代理方法，可以根据实际情况配置。

## 运行
```
docker run -d \
--name dc \
-p 3306:3306 \
-it dependencycheck-mysql:v1
```
## 升级
升级已经做成定时任务，但是升级模块可能会出一些玄学问题，建议先手动执行命令进行升级。
在/dependencycheck/目录下面执行以下指令进行更新。
```
./gradlew --no-daemon -b database.gradle update
```

## 参考
- [https://github.com/stefanneuhaus/dependencycheck-central-mysql-docker](https://github.com/stefanneuhaus/dependencycheck-central-mysql-docker)
