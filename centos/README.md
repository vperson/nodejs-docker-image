# nodejs-docker-image
使用docker运行node pdf服务，已经解决中文不显示和中文乱码问题。

* 时区已经全部调整为上海
* yum源使用的是阿里云的


## 构建镜像
```
docker build -t node:centos-v1 .
```

## 运行镜像
```
docker run -ti --rm node:centos-v1 /bin/bash
```
