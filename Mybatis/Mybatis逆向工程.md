# Mybatis逆向工程

> Gitee:https://gitee.com/boy-maofeiyu/mybatis-generator.git

## 1. 介绍	

Mybatis是目前非常流行的持久层框架，其逆向工程更是大大缩减了我们的开发时间。

所谓mybatis逆向工程，就是Mybatis会根据我们设计好的数据表，自动生成**pojo（实体）**、**mapper（接口）**以及**mapper.xml（映射）**

而且会在文件中给我们`生成单表增删改查的方法和sql`

![image-20201211164421070](https://i0.hdslb.com/bfs/album/30eb52c4a7ffde310414eb09b1acf232ea25818b.png) 



## 2.  插件使用

### 2.1  引入依赖 mybatis-generator

```xml
    <dependencies>
          <!--必要-->
        <dependency>
            <groupId>org.mybatis.generator</groupId>
            <artifactId>mybatis-generator-core</artifactId>
            <version>1.3.7</version>
        </dependency>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.5.1</version>
        </dependency>
         <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.6</version>
        </dependency>
        <!--非必要-->
        <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
            <version>1.2.17</version>
        </dependency>
		<dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
              <!--mybatis-generator的Maven插件-->
            <plugin>
                <groupId>org.mybatis.generator</groupId>
                <artifactId>mybatis-generator-maven-plugin</artifactId>
                <version>1.3.7</version>
                <configuration>
                    <verbose>true</verbose>
                    <overwrite>true</overwrite>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                    <encoding>UTF-8</encoding>
                </configuration>
            </plugin>
        </plugins>
    </build>
```



### 2.2 加入配置文件 

> 将资料包下的generatorConfig.xml 拷贝到 项目的resouces下

#### 2.2.1 文件名称:`generratorConfig.xml`

```xml


<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE generatorConfiguration PUBLIC
        "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd" >
<generatorConfiguration>
    <!-- classPathEntry:数据库的 JDBC驱动的jar 包地址 -->
    <classPathEntry location="lib/mysql-connector-java-5.1.47.jar"/>

    <!--生成java代码-->
    <context id="context" targetRuntime="MyBatis3">

        <!-- 配置生成pojo的序列化的插件-->
        <plugin type="org.mybatis.generator.plugins.SerializablePlugin"/>

        <!-- 配置生成toString的序列化的插件  -->
        <plugin type="org.mybatis.generator.plugins.ToStringPlugin"/>

        <commentGenerator>
            <!-- 是否去除自动生成的（english）注释 true：是 ： false:否 -->
            <property name="suppressAllComments" value="true"/>
        </commentGenerator>

        <!--数据库连接的信息：驱动类、连接地址、用户名、密码 -->
        <jdbcConnection driverClass="com.mysql.jdbc.Driver"
                        connectionURL="jdbc:mysql://localhost:3306/spring_141"
                        userId="root"
                        password="root"/>

        <!-- 指定生成的实体类的存放位置 -->
        <javaModelGenerator targetPackage="com.itheima.domain" targetProject="./src/main/java">
            <property name="enableSubPackages" value="true"/>
            <property name="trimStrings" value="true"/>
        </javaModelGenerator>

        <!-- 指定生成的Dao映射文件的存放位置 -->
        <sqlMapGenerator targetPackage="com.itheima.dao" targetProject="./src/main/resources">
            <property name="enableSubPackages" value="false"/>
        </sqlMapGenerator>

        <!--指定生成的Dao接口的存放位置-->
        <javaClientGenerator targetPackage="com.itheima.dao" targetProject="./src/main/java" type="XMLMAPPER">
            <property name="enableSubPackages" value="false"/>
        </javaClientGenerator>

        <!-- 指定数据库表 -->
        <table tableName="account" domainObjectName="Account" mapperName="AccountDao"
               enableCountByExample="false" enableDeleteByExample="false"
               enableSelectByExample="true" enableUpdateByExample="false"/>

    </context>
</generatorConfiguration>
```



> 拷贝测试用配置文件

#### 2.2.2 文件名称:`mybatis-config.xml`

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <!--数据库环境信息-->
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql:///spring"/>
                <property name="username" value="root"/>
                <property name="password" value="root"/>
            </dataSource>
        </environment>
    </environments>

    <!--mapper映射文件-->
    <mappers>
        <package name="com.itheima.dao"/>
    </mappers>
</configuration>
```



![image-20210609092556130](https://i0.hdslb.com/bfs/album/d99898cc94254c2610b313f104836069ba58eae1.png)

#### 2.2.3 手动加入mysql-connector的jar包

![image-20210816161734200](https://i0.hdslb.com/bfs/album/0b3e9bfac472ba2070a366c74dcf0ed77f7ab907.png)



### 2.3 运行插件，生成文件  

![image-20201220115506038](https://i0.hdslb.com/bfs/album/5f5bc15b03b8d257f597497f62aff3a62b824a1a.png) 



## 3. 生成的文件的使用

### 3.1 基础操作

~~~java
public interface AccountDao {
    //保存
    int insert(Account record);

    //动态sql的保存
    int insertSelective(Account record);

    //主键修改
    int updateByPrimaryKey(Account record);

    //动态sql的主键修改
    int updateByPrimaryKeySelective(Account record);

    //根据主键删除
    int deleteByPrimaryKey(Integer aid);

    //主键查询
    Account selectByPrimaryKey(Integer aid);

    //条件查询
    List<Account> selectByExample(AccountExample example);
}
~~~

### 3.2 条件查询

**模板代码,直接复制使用即可**

~~~java
public class MyBatisTest {
    private SqlSession sqlSession;

    @Before
    public void getSqlSession() {
        InputStream stream = null;
        try {
            stream = Resources.getResourceAsStream("mybatis-config.xml");
        } catch (IOException e) {
            e.printStackTrace();
        }
        SqlSessionFactory factory = new SqlSessionFactoryBuilder().build(stream);
        sqlSession = factory.openSession(true);
    }

    @After
    public void closeSqlSession() {
        sqlSession.close();
    }

    @Test
    public void test1() {
        AccountDao accountDao = sqlSession.getMapper(AccountDao.class);
        AccountExample example = new AccountExample();

    }
}
~~~

**引入配置文件**,修改数据库配置信息

**测试代码**

~~~java
package com.itheima.test;

import com.itheima.dao.AccountDao;
import com.itheima.domain.AccountExample;
import org.apache.ibatis.io.Resources;
import org.apache.ibatis.session.SqlSession;
import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.ibatis.session.SqlSessionFactoryBuilder;
import org.junit.After;
import org.junit.Before;
import org.junit.Test;

import java.io.IOException;
import java.io.InputStream;

/*
    AccountExample 这哥们有三个功能
    1 条件查询
        example.createCriteria().条件
    2 排序
       example.setOrderByClause(排序条件) 
    3 去重
        example.setDistinct(true);
*/
public class MybatisTest {
    private SqlSession sqlSession;

    @Before
    public void getSqlSession() {
        InputStream stream = null;
        try {
            stream = Resources.getResourceAsStream("mybatis-config.xml");
        } catch (IOException e) {
            e.printStackTrace();
        }
        SqlSessionFactory factory = new SqlSessionFactoryBuilder().build(stream);
        sqlSession = factory.openSession(true);
    }

    @After
    public void closeSqlSession() {
        sqlSession.close();
    }

    @Test
    public void test1() {
        AccountDao accountDao = sqlSession.getMapper(AccountDao.class);
        AccountExample example = new AccountExample();

        //这是example的一个小弟,作用是用于条件的拼接
        AccountExample.Criteria criteria = example.createCriteria();
//        criteria.andAidGreaterThan(2);//where aid > 2
//        criteria.andBalanceBetween(10f,100f);//WHERE ( aid > 2 and balance between 1 and 100 )
//        criteria.andNameLike("B%");//WHERE ( aid > ? and balance between ? and ? and name like B% )

        criteria.andAidGreaterThan(2).andBalanceBetween(10f, 100f).andNameLike("B%");

        accountDao.selectByExample(example);
    }


    @Test
    public void test2() {
        AccountDao accountDao = sqlSession.getMapper(AccountDao.class);
        AccountExample example = new AccountExample();

        //这是example的一个小弟,作用是用于排序
        example.setOrderByClause("aid desc");//from account order by aid desc
        accountDao.selectByExample(example);
    }

    @Test
    public void test3() {
        AccountDao accountDao = sqlSession.getMapper(AccountDao.class);
        AccountExample example = new AccountExample();

        //这是example的一个小弟,作用是用于去重
        example.setDistinct(true);
        accountDao.selectByExample(example);
    }
} 
~~~

### 3.3 模板说明

>~~~markdown
>* 条件说明
>* criteria.andXxxIsNull    添加字段xxx为null的条件
>* criteria.andXxxIsNotNull    添加字段xxx不为null的条件
>* criteria.andXxxEqualTo(value)    添加xxx字段等于value条件
>* criteria.andXxxNotEqualTo(value)    添加xxx字段不等于value条件
>* criteria.andXxxGreaterThan(value)    添加xxx字段大于value条件
>* criteria.andXxxGreaterThanOrEqualTo(value)    添加xxx字段大于等于value条件
>* criteria.andXxxLessThan(value)    添加xxx字段小于value条件
>* criteria.andXxxLessThanOrEqualTo(value)    添加xxx字段小于等于value条件
>* criteria.andXxxIn(List<？>)    添加xxx字段值在List<？>条件
>* criteria.andXxxNotIn(List<？>)    添加xxx字段值不在List<？>条件
>* criteria.andXxxLike(“%”+value+”%”)    添加xxx字段值为value的模糊查询条件
>* criteria.andXxxNotLike(“%”+value+”%”)    添加xxx字段值不为value的模糊查询条件
>* criteria.andXxxBetween(value1,value2)    添加xxx字段值在value1和value2之间条件
>* criteria.andXxxNotBetween(value1,value2)    添加xxx字段值不在value1和value2之间条件
>~~~

