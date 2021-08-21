# Mybatis-Plus代码生成器

## pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <packaging>jar</packaging>

    <!--父工程-->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.4.RELEASE</version>
    </parent>

    <groupId>com.itheima</groupId>
    <artifactId>mybatis-plus-generator</artifactId>
    <version>1.0-SNAPSHOT</version>


    <dependencies>
        <!--springBoot测试-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>

        <!--mybatis-plus的springboot支持-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.1.1</version>
        </dependency>
        <!--mybatis-plus-generator生成器支持-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-generator</artifactId>
            <version>3.1.1</version>
        </dependency>
        <!--mybatis-plus模板引擎支持-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-freemarker</artifactId>
        </dependency>
        <!--mysql驱动-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.47</version>
        </dependency>
        <!--log4j日志-->
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-log4j12</artifactId>
        </dependency>
    </dependencies>

</project>
```

## java代码

```java
package generator;

import com.baomidou.mybatisplus.core.exceptions.MybatisPlusException;
import com.baomidou.mybatisplus.core.toolkit.StringPool;
import com.baomidou.mybatisplus.core.toolkit.StringUtils;
import com.baomidou.mybatisplus.generator.AutoGenerator;
import com.baomidou.mybatisplus.generator.InjectionConfig;
import com.baomidou.mybatisplus.generator.config.*;
import com.baomidou.mybatisplus.generator.config.po.TableInfo;
import com.baomidou.mybatisplus.generator.config.rules.NamingStrategy;
import com.baomidou.mybatisplus.generator.engine.FreemarkerTemplateEngine;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

/**
 * <p>
 * mysql 代码生成器演示例子
 * </p>
 */
public class MysqlGenerator {

    /**
     * <p>
     * 读取控制台内容
     * </p>
     */
    public static String scanner(String tip) {
        Scanner scanner = new Scanner(System.in);
        StringBuilder help = new StringBuilder();
        help.append("请输入" + tip + "：");
        System.out.println(help.toString());
        if (scanner.hasNext()) {
            String ipt = scanner.next();
            if (StringUtils.isNotEmpty(ipt)) {
                return ipt;
            }
        }
        throw new MybatisPlusException("请输入正确的" + tip + "！");
    }

    /**
     * RUN THIS
     */
    public static void main(String[] args) {
        // 代码生成器
        AutoGenerator mpg = new AutoGenerator();

        // 全局配置
        GlobalConfig gc = new GlobalConfig();
        String projectPath = System.getProperty("user.dir");
        gc.setOutputDir(projectPath + "/src/main/java");
        gc.setAuthor("boy-maofeiyu");
        gc.setOpen(false);
        mpg.setGlobalConfig(gc);

        // 数据源配置
        DataSourceConfig dsc = new DataSourceConfig();

        /*数据库配置*/
        dsc.setUrl("jdbc:mysql://localhost:3306/mp?useUnicode=true&useSSL=false&characterEncoding=utf8");
        // dsc.setSchemaName("public");
        dsc.setDriverName("com.mysql.jdbc.Driver");
        dsc.setUsername("root");
        dsc.setPassword("123456");
        mpg.setDataSource(dsc);

        // 包配置
        PackageConfig pc = new PackageConfig();
        pc.setModuleName(scanner("请输入模块名"));
        pc.setParent("com.itheima");
        mpg.setPackageInfo(pc);

        // 自定义配置
        InjectionConfig cfg = new InjectionConfig() {
            @Override
            public void initMap() {
                // to do nothing
            }
        };
        List<FileOutConfig> focList = new ArrayList<>();
        focList.add(new FileOutConfig("/templates/mapper.xml.ftl") {
            @Override
            public String outputFile(TableInfo tableInfo) {
                // 自定义输入文件名称  获取输入模块名称pc.getModuleName()
                return projectPath + "/src/main/resources/com/itheima/" + pc.getModuleName()+"/dao"
                        + "/" + tableInfo.getEntityName() + "Dao" + StringPool.DOT_XML;
            }
        });
        cfg.setFileOutConfigList(focList);
        mpg.setCfg(cfg);
        mpg.setTemplate(new TemplateConfig().setXml(null));

        // 策略配置
        StrategyConfig strategy = new StrategyConfig();
        strategy.setNaming(NamingStrategy.underline_to_camel);
        strategy.setColumnNaming(NamingStrategy.underline_to_camel);
//        strategy.setSuperEntityClass("com.baomidou.mybatisplus.samples.generator.common.BaseEntity");
        strategy.setEntityLombokModel(true);
//        strategy.setSuperControllerClass("com.baomidou.mybatisplus.samples.generator.common.BaseController");
        strategy.setInclude(scanner("表名"));
        strategy.setSuperEntityColumns("id");
        strategy.setControllerMappingHyphenStyle(true);
        strategy.setTablePrefix(pc.getModuleName() + "_");
        mpg.setStrategy(strategy);
        // 选择 freemarker 引擎需要指定如下加，注意 pom 依赖必须有！
        mpg.setTemplateEngine(new FreemarkerTemplateEngine());
        mpg.execute();
    }

}
```





## 添加依赖

MyBatis-Plus 从 `3.0.3` 之后移除了代码生成器与模板引擎的默认依赖，需要手动添加相关依赖

* 添加`代码生成器`依赖

  ```xml
  <dependency>
      <groupId>com.baomidou</groupId>
      <artifactId>mybatis-plus-generator</artifactId>
      <version>3.4.1</version>
  </dependency>
  ```

* 添加模板引擎依赖,Mybatis-Plus支持Velocity（默认）、Freemarker、Beetl，用户可以选择自己熟悉的模板引擎，如果都不满足您的要求，可以采用自定义模板引擎

![image-20210821162345753](https://i0.hdslb.com/bfs/album/0d2963034bf3fcaaed024a40111b617bb1c23e42.png)

注意！如果您选择了非默认引擎，需要在 AutoGenerator 中 设置模板引擎

```java
AutoGenerator generator = new AutoGenerator();

// set freemarker engine
generator.setTemplateEngine(new FreemarkerTemplateEngine());

// set beetl engine
generator.setTemplateEngine(new BeetlTemplateEngine());

// set custom engine (reference class is your custom engine class)
generator.setTemplateEngine(new CustomTemplateEngine());

// other config
...
```



## 编写配置

MyBatis-Plus 的代码生成器提供了大量的自定义参数供用户选择，能够满足绝大部分人的使用需求

* 配置GlobalConfig

  ```java
  GlobalConfig globalConfig = new GlobalConfig();
  globalConfig.setOutputDir(System.getProperty("user.dir") + "/src/main/java");
  globalConfig.setAuthor("jobob");
  globalConfig.setOpen(false);
  ```

* 配置 DataSourceConfig

  ```java
  DataSourceConfig dataSourceConfig = new DataSourceConfig();
  dataSourceConfig.setUrl("jdbc:mysql://localhost:3306/ant?useUnicode=true&useSSL=false&characterEncoding=utf8");
  dataSourceConfig.setDriverName("com.mysql.jdbc.Driver");
  dataSourceConfig.setUsername("root");
  dataSourceConfig.setPassword("password");
  ```

  

## 自定义代码模板

```java
//指定自定义模板路径, 位置：/resources/templates/entity2.java.ftl(或者是.vm)
//注意不要带上.ftl(或者是.vm), 会根据使用的模板引擎自动识别
TemplateConfig templateConfig = new TemplateConfig()
    .setEntity("templates/entity2.java");

AutoGenerator mpg = new AutoGenerator();
//配置自定义模板
mpg.setTemplate(templateConfig);
```



## 自定义属性注入

```java
InjectionConfig injectionConfig = new InjectionConfig() {
    //自定义属性注入:abc
    //在.ftl(或者是.vm)模板中，通过${cfg.abc}获取属性
    @Override
    public void initMap() {
        Map<String, Object> map = new HashMap<>();
        map.put("abc", this.getConfig().getGlobalConfig().getAuthor() + "-mp");
        this.setMap(map);
    }
};
AutoGenerator mpg = new AutoGenerator();
//配置自定义属性注入
mpg.setCfg(injectionConfig);
```

## 字段其他信息查询注入

![relationship](https://mp.baomidou.com/img/custom-fields.png)

```java
new DataSourceConfig().setDbQuery(new MySqlQuery() {

    /**
     * 重写父类预留查询自定义字段<br>
     * 这里查询的 SQL 对应父类 tableFieldsSql 的查询字段，默认不能满足你的需求请重写它<br>
     * 模板中调用：  table.fields 获取所有字段信息，
     * 然后循环字段获取 field.customMap 从 MAP 中获取注入字段如下  NULL 或者 PRIVILEGES
     */
    @Override
    public String[] fieldCustom() {
        return new String[]{"NULL", "PRIVILEGES"};
    }
})
```