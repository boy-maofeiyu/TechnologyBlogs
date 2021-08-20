![006GJQvhgy1gsaixdrdinj30u00u0dma](https://i0.hdslb.com/bfs/album/0751dfb1837eb9ac5e727e7b93bbdaca82913b1c.jpg)

> 20级不知名软件工程学长,给学弟学妹Java开学第一课见面礼

# 一. JavaSE下载

## 1. 百度搜索Oracle

![image-20210805183405221](https://i0.hdslb.com/bfs/album/494fe8dbefd7fd7cce5ac3aadc0474bf229b46e3.png)

## 2. 找到Oracle(甲骨文公司官网)

![image-20210805183433273](https://i0.hdslb.com/bfs/album/a5666e59a5e9b9b5f378df1a568b53fa59ea6690.png)



## 3. 点击Products

网址:https://www.baidu.com/link?url=WH6UPiM9qpDNZop20EVL3NJs6CnLeLhPhS7eMh0pIQ_tNWYi5fhtIihRcbLuRuB8&wd=&eqid=b4a4fdfc000673c100000004610bc271

![image-20210805183531257](https://i0.hdslb.com/bfs/album/eab3e5fbba7abc969d32210a69091056357fb31c.png)

## 4. 点击Java

![image-20210805183545741](https://i0.hdslb.com/bfs/album/b05f6f3ff62bd860e75188dd689423ae7ede8869.png)

## 5. 点击下载Java文件

网址:https://www.oracle.com/java/

![image-20210805183727254](https://i0.hdslb.com/bfs/album/e9999b76d8877a1eb41ac04fb4862b36870c49b2.png)

## 6. 下载JavaSE

### 为什么安装JDK8?

网址;https://www.oracle.com/java/technologies/javase-downloads.html

目前Java已经更新到Java16,但是目前在企业中Java8更常用,且经过时间的考量,Java8是目前Java版本中最稳定的,所以我们寻找Java SE 8 版本

![image-20210805184121736](https://i0.hdslb.com/bfs/album/858f4db4b9b9785c4033c12ab32c86bc43b213d7.png)

### 我们为什么不安装下面的JRE呢?

>  因为JDK包含JRE

![image-20210805184325664](https://i0.hdslb.com/bfs/album/84773476727a24ec3c351743d572c17bb7ed07de.png)

JDK是 Java 语言的软件开发工具包，主要用于移动设备、嵌入式设备上的java应用程序。JDK是整个java开发的核心，它包含了JAVA的运行环境（JVM+Java系统类库）和JAVA工具。

JRE是Java Runtime Environment缩写，指Java运行环境，是Sun的产品。运行JAVA程序所必须的环境的集合，包含JVM标准实现及Java核心类库。注意由于Microsoft对Java的支持不完全，请不要使用IE自带的虚拟机来运行 Applet，务必安装一个JRE或JDK。

## 7. 点击JDK Download跳转到下载页面

> 选择匹配自己电脑操作系统种类的版本

网址:https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html

![image-20210805184916298](C:/Users/15745/AppData/Roaming/Typora/typora-user-images/image-20210805184916298.png)

## 8. 点击下载跳转到登陆页面

网址:https://login.oracle.com/mysso/signon.jsp

![image-20210805185352411](https://i0.hdslb.com/bfs/album/b19dcc3d954b7bbbfdd4e33402881c8c4ab7306f.png)

## 9. 下载完成

![image-20210805185810943](https://i0.hdslb.com/bfs/album/7b0b9b03171b32c92fde029f9d2a757a47bd2ff3.png)

# 二. 开始安装

### 1. 新建JDK安装目录

![image-20210805190014220](https://i0.hdslb.com/bfs/album/b0c13c70bc20144bee8463df841648387e9b99c9.png)

![image-20210805190057315](https://i0.hdslb.com/bfs/album/be6c377953b31857f36399a553e35fbdb9f84d79.png)

### 2. 双击jdk程序安装

![image-20210805185847493](https://i0.hdslb.com/bfs/album/30810449e4854ac40c6b361b5722fae0a90dd436.png)

### 3. 更改JDK安装路径

![image-20210805185938988](https://i0.hdslb.com/bfs/album/e29e0b6ddfe134522cac223b3657474150a04bc8.png)

![image-20210805190152675](https://i0.hdslb.com/bfs/album/4a5cf42df5b167274db6c65d90b9088bc4f7531e.png)



### 			4. 点击下一步等待安装完成

​		![image-20210805190232525](https://i0.hdslb.com/bfs/album/dbeb3d88b0fc291e309fee8e15a9d1940df63414.png)

![image-20210805190331101](https://i0.hdslb.com/bfs/album/a9be8b4e39fd0929ca87e1c2d07e99ee237a9267.png)



# 三. Java环境变量配置

> 作用:在计算机任意目录位置,都能通过命令行立刻运行程序

### 为什么要配置环境变量?

从接触 java 开始，就被配置环境变量所困扰，每换一个新环境总要上网搜前人的配置经验。至于为什么要配、配什么一直都是一知半解，今天做一下总结，简单明了介绍一下：

```
环境变量是在操作系统中一个具有特定名字的对象，它包含了一个或者多个应用程序所将使用到的信息。
```



#### 一、环境变量怎么配置

在初次安装Java后，为了更加方便的使用需要配置环境变量，或者说安装了新版本的JDK后，使用java -version查看发现还是之前的版本，这也是环境变量配置的原因。

通常情况我们需要配置以下三个变量：

- `JAVA_HOME`：指向Jdk的安装目录，作用是一些基于Java开发的工具会用到，比如tomcat,Eclipse，如果不用这些工具不需要配置。
- `Path`：指向jdk安装目录下的bin目录，作用是指定命令搜索路径，bin目录下有编译、启动（javac/java）等命令，为了任何目录位置下都可以直接输入命令，而不用输入长长的路径了。如果配置了JAVA _HOME ，直接把%JAVA_HOME%/bin追加到PATH中即可。
- `CLASSPATH`：在于告诉Java执行环境，在哪些目录下可以找到我们所要执行的Java程序所需要的类或者包。不过在JDK1.5之后的版本完全可以不用设置classpath环境变量就能正常运行程序。

#### 二、为什么要配置`环境变量`

windows系统下，假如我们安装了某一款软件，安装结束后，在安装目录会生成一个该软件的.exe文件，双击该文件，我们就能启动软件。但是难道我们每次要运行该软件的时候都要`先找到该.exe文件所在的路径`，然后双击吗，显然是不可能的，`因为安装的软件太多，我们根本不可能记住所有已安装软件的路径。`
这时候就需要`环境变量`了。

#### 三、什么工具需要配置

任何工具都可以配置。

`配置的目的就是快速的打开、使用软件`。有一些工具需要指定的变量名，这个就要看说明文档后在做配置。

#### 四、环境变量中`用户变量`和`系统变量`的区别

系统变量：配置以后，整个计算机操作系统有效。

用户变量：配置以后，对于当前计算机用户有效。

二者本质都是变量，系统变量针对所有用户，而用户变量是当前用户私有的。



## 1. 第一种方式

### 1.1    右击此电脑------点击属性

![image-20210805190703834](https://i0.hdslb.com/bfs/album/129345021c1fbf84016e48ab0eeb1d7fb413b2a8.png)

### 1.2 点击高级------点击环境变量

![image-20210805190825564](https://i0.hdslb.com/bfs/album/1c3c8acc916466885c5b015068c0970c5527ac02.png)

### 1.3 打开环境变量配置文件

![image-20210805190904174](https://i0.hdslb.com/bfs/album/a378547f841be1f3a5dfff2f3c479ded22d390a8.png)



## 2. 第二种方式

### 2.1 点击设置

![image-20210805191127100](https://i0.hdslb.com/bfs/album/24844e0d29d8e73bb0e3049078e3e836c19e5fd8.png)

### 2.2搜索环境变量

![image-20210805191250111](https://i0.hdslb.com/bfs/album/d4e34be99987899b5f31d0b00b9f210d0c6bdd02.png)

### 2.3 点击高级------点击环境变量

![image-20210805190825564](https://i0.hdslb.com/bfs/album/1c3c8acc916466885c5b015068c0970c5527ac02.png)

### 2.4 打开环境变量配置文件

![image-20210805190904174](https://i0.hdslb.com/bfs/album/a378547f841be1f3a5dfff2f3c479ded22d390a8.png)

## 3.  第三种方式`Mac安装`

> 网址:https://blog.csdn.net/u014801367/article/details/86288078

# 四. 配置开始

## 1. 新建JAVA_HOME变量

![image-20210805191620987](https://i0.hdslb.com/bfs/album/e03fb9ddce3f6828efa2ea0cf052992bd5fa3cd3.png)

输入:

```
变量名：JAVA_HOME
变量值：电脑上JDK安装的绝对路径.例如:D:\jdk8
```

## 注意

> JDK 路径下必须能够看到如下的文件

![image-20210805192012758](https://i0.hdslb.com/bfs/album/b7ed170f4ab679138e83b98edc01c40d51faed1a.png)

输入完毕后:点击 OK

![image-20210805191820667](https://i0.hdslb.com/bfs/album/d154123d7310723546f8d7272762dc916e847e05.png)

## 2. 新建/修改CLASSPATH变量

如果存在 **CLASSPATH** 变量，选中点击 **Edit(编辑)**

如果没有，点击 **New（新建）...** 新建。

输入/在已有的变量值后面添加：

```
变量名：CLASSPATH
变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
```

![image-20210805192310513](https://i0.hdslb.com/bfs/album/6629ffc83bd97c11df13a086ddc057eeafc622f5.png)



## 3. 修改Path变量

由于 win10 的不同，当选中 **Path** 变量的时候，系统会很方便的把所有不同路径都分开了，不会像 win7 或者 win8 那样连在一起。

![image-20210805192546986](https://i0.hdslb.com/bfs/album/ab5ab5cefbc17115873a1fd9414b28dbb1f1a2a0.png)

新建两条路径：

```
%JAVA_HOME%\bin
%JAVA_HOME%\jre\bin
```

![image-20210805192600834](https://i0.hdslb.com/bfs/album/6252b4cfafc725c30496b175906f13c66ff49f3d.png)



# 五. 检验是否安装成功

> 命令行打开方式:win+R    输入cmd

### 1. 输入 **java**，出现一连串的指令提示，说明配置成功了

![image-20210805192657754](https://i0.hdslb.com/bfs/album/09ba4f1e3d33e4fb12a4fec76ae2bfe866e390cb.png)

### 	2. 再次输入javac,出现一连串的指令提示，说明配置成功了

![image-20210805192723067](https://i0.hdslb.com/bfs/album/80ce16f1d380449abdf8862079579cc8784833dd.png)



# 六.  JDK下载地址(高速)

JDK8`阿里云盘下载`:https://www.aliyundrive.com/s/fr2Xb9eGaXm

国内JDK下载地址:https://www.programmer-box.com/?ref=jdk_1.8

# 七. 安装失败`如何卸载`

> geek强力卸载:自动卸载软件,不会残留任何的 `注册表和缓存` 数据

geek强力卸载`阿里云盘地址`**https://www.aliyundrive.com/s/2sVZ65FGFzj**

![image-20210805195256350](https://i0.hdslb.com/bfs/album/94b207c239f9affdea9dc1b399f9d37ea8c45b8b.png)