# Maven基础

## 一. Maven是什么?

* 本质是一个项目管理工具,将项目开发和管理过程抽象成一个项目对象模型(POM)
* POM(Project Object Model):项目对象模型

![image-20210819112522459](https://i0.hdslb.com/bfs/album/179d4e76a2273a52288e6112d76a574a232fba25.png)



## 二.Maven作用 

* 项目构建:提供标准的,跨平台的`自动化`项目构建方式
* 依赖管理:方便快捷的管理项目依赖的资源`jar包`,避免资源间`版本冲突`的问题



## 三.Maven下载安装

省略

## 四.Maven仓库

### 1.仓库概念

![image-20210819113128973](https://i0.hdslb.com/bfs/album/17ecacee864f2b57b1b9281ed78d9437e12be6ed.png)

![image-20210819113254597](https://i0.hdslb.com/bfs/album/df17c2c46706e3817bbd7470aaec0262457fdf89.png)



### 2.坐标

* 什么是坐标? Maven中坐标用来描述参股中资源位置

* Maven坐标主要组成:

  groupId:定义当前Maven项目的隶属组织名称(通常是域名反写)

  artifactId:定义当前Maven项目的名称(通常是模块名称)

  version:定义当前项目的版本号

  packing:定义当前项目的打包方式

* Maven坐标作用:使用的唯一标识,识别资源位置

### 3.Maven仓库配置

* 本地仓库配置
* 阿里云镜像仓库配置

## 五.Maven项目结构

![image-20210819114742021](https://i0.hdslb.com/bfs/album/37c444a77871ea11d1f02d9291391b1a65ac2546.png)

![image-20210819120512453](https://i0.hdslb.com/bfs/album/2166a942f047dc999900df08825cf98494c76c94.png)



## 六.tomact插件配置

```xml
 <build>
        <plugins>
            <plugin>
                <groupId>org.apache.tomcat.maven</groupId>
                <artifactId>tomcat7-maven-plugin</artifactId>
                <version>2.1</version>
                <configuration>
                    <port>80</port>
                    <path>/</path>
                </configuration>
            </plugin>
        </plugins>
    </build>

```

### 1.第一种

![image-20210819131006186](https://i0.hdslb.com/bfs/album/b84e5f4d865fc164bca59bc9f0930f949569af4c.png)

### 2.第二种

![image-20210819130927174](https://i0.hdslb.com/bfs/album/63c66d30c8b4cedf5fbad70cfd9e9f473526ff14.png)



## 七.依赖管理-依赖配置和依赖传递

### 1.依赖传递

![image-20210819131413986](https://i0.hdslb.com/bfs/album/c41ee7e7f9aeb4fbc9ff98fd052729e53b2d0750.png)





### 2.依赖传递冲突问题

* 路径优先:当依赖中出现相同的资源时,层级越深,优先级越低,层级越浅,优先级越高
* 声明优先:当资源在相同层级被依赖时,配置顺序靠前的覆盖配置顺序靠后的
* 特殊优先:当同级配置了相同资源的不同版本,后配置的覆盖先配置的



### 3.排除依赖  主动  or  被动

被动

![image-20210819132014360](https://i0.hdslb.com/bfs/album/b379cfb86ca680df38e6a80b59c06dbaee16f128.png)



主动

![image-20210819132138951](https://i0.hdslb.com/bfs/album/e1cb7e749809c33754f9bc5c4a4a06a60568e92b.png)



### 4.依赖范围

![image-20210819132456807](https://i0.hdslb.com/bfs/album/7f9ab5de73a366e21c10accfa4960277c6afcdb7.png)



![image-20210819132713064](https://i0.hdslb.com/bfs/album/a85b21288d0b2ed877c00b7ae9a726e69c6abe9a.png)



### 5.依赖范围的传递性 `了解`

![image-20210819133049923](https://i0.hdslb.com/bfs/album/e21d5eb919492b0f7ae31f742a4e76e202ef3dc4.png)





## 八.生命周期与插件

![image-20210819160807909](https://i0.hdslb.com/bfs/album/86d954b8b30cecd91c8fefb0041e0bcda2cec806.png)

![image-20210819160835243](https://i0.hdslb.com/bfs/album/7645d32f9c28f3ba61748a04b2d88ce7d7985c4c.png)

![image-20210819160821933](https://i0.hdslb.com/bfs/album/387e95a118d6fde7e9bcf817ab5b87937ec3be21.png)

![image-20210819160846789](https://i0.hdslb.com/bfs/album/b749e6ef0a416c7984cb4f6b414fba7926f7576c.png)

![image-20210819134703184](https://i0.hdslb.com/bfs/album/32bad5167d63433a499543c3779dfa5fb4a2f79c.png)



![image-20210819160928956](https://i0.hdslb.com/bfs/album/98024f575bbf2768b3e474c9b5713fdc721881f6.png)





# Maven高级

## 1.工程模块与模块划分

![image-20210819161510509](https://i0.hdslb.com/bfs/album/349e82508c39537d0e5a98b3fdd91bad72b047cf.png)



## 2.分模块开发设计

### POJO

![image-20210819161535713](https://i0.hdslb.com/bfs/album/c55cb437783abd8988bc0660c7b848a90fd18eb8.png)

### DAO

![image-20210819161546298](https://i0.hdslb.com/bfs/album/6a46809c4c63ac5d75a4e5ee253f348da5822bbb.png)



### SERVICE

![](https://i0.hdslb.com/bfs/album/c8550268d330bc776f821197d4563ad93b28e6c3.png)

### CONTROLLER

![image-20210819161800828](https://i0.hdslb.com/bfs/album/86f0cec353bfb16d59aec4137f1c6b577bbee00e.png)



## 3.聚合   `子工程同时打包安装部署`

![image-20210819162339352](https://i0.hdslb.com/bfs/album/04b561d33320c0f7a2dc475c6a3552d7cc6b2a90.png)

![image-20210819162400272](https://i0.hdslb.com/bfs/album/e37f40fefc07ae0a7abd8d9d14bdacaa51840e95.png)



## 4.继承

![image-20210819163109463](https://i0.hdslb.com/bfs/album/aa967ac48b62aa5b30062d30ea4bc7050a0daee2.png)

### 继承作用方式

![image-20210819163121001](https://i0.hdslb.com/bfs/album/73804eb892799dc92fc9e09572f194ba4e0d2d3e.png)

### 继承依赖定义

![image-20210819163202518](https://i0.hdslb.com/bfs/album/451c8abf26e8ea3d9d976020bb2d1ffe39fc521a.png)

### 继承依赖使用

![image-20210819163215607](https://i0.hdslb.com/bfs/album/1b1b44a9bc824654fd01b1eb0ba30fc43a1a5e60.png)



### 继承的资源

![image-20210819163237569](https://i0.hdslb.com/bfs/album/8fd300ce6cff88a1f8bf62eb16d842275b1f6d4d.png)



## 5.继承和聚合

![image-20210819163447191](https://i0.hdslb.com/bfs/album/95dbaac9b3174a7ef1b193d2cb7061e30fba1ccc.png)



## 6.属性

![image-20210819163643695](https://i0.hdslb.com/bfs/album/6b9cc2ead17af56b38034e310fe6cbcad6bb1066.png)



### 自定义属性

![image-20210819163713111](https://i0.hdslb.com/bfs/album/7dd6fe1b163851162052ef13a8662eab8520994c.png)



### 内置属性



![image-20210819163728511](https://i0.hdslb.com/bfs/album/7c416ac5d493cc9b225fc192e737ab23f2368f24.png)

![image-20210819163755834](https://i0.hdslb.com/bfs/album/4829ff0147d2b0ef9e40164b234387184b60690a.png)

![image-20210819163803749](https://i0.hdslb.com/bfs/album/06138aded60f3f177169c6630b462db4c85374a8.png)

![image-20210819163812314](https://i0.hdslb.com/bfs/album/782b0c5d4f3ff237ceabae769a45123b0ea7cf68.png)



## 7.版本管理

![image-20210819163916646](https://i0.hdslb.com/bfs/album/49bf080c4514dcce1b03f21692e1b6285c96fcc4.png)

![image-20210819163928184](https://i0.hdslb.com/bfs/album/8112769ffcee6e970f617b140f5d358d69e5153a.png)



## 8.资源文件配置

### 资源配置多文件维护

![image-20210819164027526](https://i0.hdslb.com/bfs/album/8320883194c53eb5c6c5bee3c9466d834b07351c.png)





### 配置文件引用pom属性

![image-20210819164105831](https://i0.hdslb.com/bfs/album/21b76f90ec1c1c1cda6615c476db08af8fa1f29c.png)

![image-20210819164622261](https://i0.hdslb.com/bfs/album/e5d741cbc4b42a2c7c5b81081b07e062b4cd78fc.png)

```xml
 <!--识别所有的配置文件-->
    <resources>
      <resource>
        <directory>src/main/java</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>false</filtering>
      </resource>
      <resource>
        <directory>${project.basedir}/src/main/resources</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>false</filtering>
      </resource>
    </resources>
```



## 9.多开发环境配置

![image-20210819165329160](https://i0.hdslb.com/bfs/album/7f428570853cc70922dd65f6b659919a1cbfed92.png)

### 多环境配置

![image-20210819165403973](https://i0.hdslb.com/bfs/album/f6697c5422876de170009b0d4efd4eb039745668.png)



### 加载指定环境

![image-20210819165517276](https://i0.hdslb.com/bfs/album/e4a5788a89bc8437f531624c2758f5f11a2ef9dd.png)



## 10.跳过测试

​	![image-20210819165716908](https://i0.hdslb.com/bfs/album/f053f2bd550828b654770a639d564156e9fd3a1c.png)

### 使用命令行跳过测试

![image-20210819165733478](https://i0.hdslb.com/bfs/album/06c3db96d659463246b2217312b4f303c7bdb546.png)

### 使用界面跳过测试

![image-20210819165746580](https://i0.hdslb.com/bfs/album/eaa89b7cd3331aae01211ae62313df52f2cd5299.png)

### 使用配置文件跳过测试

![image-20210819165803766](https://i0.hdslb.com/bfs/album/ea012e5055b0c792052ced7b00a9ff7dba4d376f.png)





# 问题?

## 1.Maven打包后各目录的含义



![image-20210819120632048](https://i0.hdslb.com/bfs/album/6e41227b3e673099b5782d12859f498ce5de4603.png)

## 2.如何解决版本冲突? 自动吗?



## 3.Maven打成jar包后各目录含义

> site生命周期作用



## 4.pom和jar和war的区别

pom：打出来可以作为其他项目的maven依赖，在工程A中添加工程B的pom，A就可以使用B中的类。用在父级工程或聚合工程中。用来做jar包的版本控制。

jar包：通常是开发时要引用通用类，打成jar包便于存放管理。当你使用某些功能时就需要这些jar包的支持，需要导入jar包。

war包：是做好一个web网站后，打成war包部署到服务器。目的是节省资源，提供效率。

## 5.Maven生命周期和插件的区别

生命周期是依靠插件执行的,内部集成调用了很多插件



## 6.maven依赖的继承体系<dependencyManagement>

不加<dependencyManagement>,依赖全部继承

加了不继承

#### 版本锁定

面对众多的依赖，有一种方法不用考虑依赖路径、声明优先等因素，可以采用直接锁定版本的方法确定依赖构件的版本

版本锁定后，系统会以锁定的版本的为准添加到工程中，此方法在企业开发中常用。



## 7.idea只是工具本质到`本地仓库`中寻找



## 8.Maven项目打包之后会不会把他依赖的jar包一起打包

## 9.如果依赖自己的本地仓库的其他jar包要是部署到其他地方是不是要一起部署
