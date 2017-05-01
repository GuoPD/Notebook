# Maven项目
初次使用Maven，记录以下具体的配置与使用过程。Maven是一个自动管理项目依赖的工具，可以进行项目的编译及打包等操作。

## Maven配置
安装好maven后，默认的maven项目依赖包缓存路径为
>/Users/admin/.m2/repository

配置时，需要注意路径下的[settings.xml](http://localhost:9000/api/file/getAttach?fileId=58fcaad231d9495046000001)文件中jar包请求地址是否正确
>/Users/admin/.m2/settings.xml

## 项目编译
进入项目所在根路径后，输入以下命令便可以对项目进行编译
```bash
mvn compile
```
编译期间，会自动检查依赖包，对缺少的依赖包自动下载到缓存路径中

## 项目打成jar包
将maven项目打包，会生成在对应target目录中，只需在项目根路径下输入
```bash
mvn install
```


