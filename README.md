# 作用：编译一个jar内置命令，可自定义，从而避免外挂start.sh。

## 最快方法

fork本项目，先去开启github action,然后编辑RunLinuxCommand.java，找到/com/example/demo/RunLinuxCommand.java，

更改57\58行为你想要执行的命令，这里基本不用转义，不过有一种情况特殊，那就是\要换成\\\\，全局替换就好。

然后提交，去github action页面等待产物生成。

## 常规方法
要编译它，第二快的方法要用idx的工作台firebase studio弄一个java的环境。

### 上传java.tar.gz，解压tar -zxvf java.tar.gz

找到/com/example/demo/RunLinuxCommand.java，更改57\58行为你想要执行的命令，这里基本不用转义，不过有一种情况特殊，那就是\要换成\\\\，全局替换就好(仅限start.sh脚本内容)。

打包编译，回到和MANIFEST.MF同级目录下，输入如下命令

### 生成class

```
javac com/example/demo/RunLinuxCommand.java
```

### 打包jar

```
jar cfm main.jar MANIFEST.MF -C . com/example/demo/RunLinuxCommand.class
```

### 测试jar是否可用，运行jar

```
java -jar main.jar
```
