# myjdk
 自用jdk镜像

# 使用方法

将如下文件上传到目标服务器同一目录下：

- build.sh
- Dockerfile
- simhei.tff

运行`sh build.sh`

将会打包为镜像`myjdk:18`

之后应用程序的`Dockerfile`只需要填写如下内容即可：

```dockerfile
FROM myjdk:18
ADD app.war app.war
ENTRYPOINT java ${JAVA_OPTS} -jar /app.war  --spring.profiles.active=prod
```

# 本镜像包含内容

- 基础镜像`openjdk:18`
- 安装了`MySQL-Client`，可以使用`mysqldump`和`mysql`指令备份和还原数据库
- 设置了时区为东八区
- 添加了中文字体`黑体`
