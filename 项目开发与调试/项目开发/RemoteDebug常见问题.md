## 代码不同步
在进行Remote Debug，单步执行遇到代码不同步问题，可能的原因有以下两点：

1. 检查生成时的依赖模块，如果使用maven管理，则可能出现使用仓库中的模块直接进行编译，而不是修改后的模块编译，因此造成调试不同步。

2. 检查pom.xml文件中的依赖关系，在video2video中，将版本号修改为本机生成的快照SNAPSHOT版，而不是采用线上的版本

针对第一种情况，将maven仓库（默认在/User/admin/.m2/repository）中删除即可。
针对第二种情况，将pom.xml中的依赖版本升级至工程生成的java包版本。

打包时，采用
>mvn clean
>mvn install
即可
