# dependencycheck-mysql-docker
## 背景
owasp官方提供了一个dependency check mysql 容器，但是受限于国内网络环境等因素，不怎么好用，这里单独开一个源供自己研究和学习使用。

## 构建
```
docker build -t dependencycheck-mysql:v1 .
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
