# JSON Web Token

## 1.什么是JWT?

JSONWebToken(JWT)是⼀个开放标准(RFC7519)，它定义了⼀种紧凑的、⾃包含的⽅式，⽤于
作为JSON对象在各⽅之间安全地传输信息。该信息可以被验证和信任，因为它是数字签名的。  

### 1.1.什么时候应该用JWT?

JSON Web Token (JWT)是⼀个开放标准(RFC7519)，它定义了⼀种紧凑的、⾃包含的⽅式，⽤于
作为JSON对象在各⽅之间安全地传输信息。该信息可以被验证和信任，因为它是数字签名的。  

### 1.2.认证流程

![image-20210827165954270](https://i0.hdslb.com/bfs/album/de866058bae2a54b59ffac51763c7c60f5a86d84.png)

![image-20210827170034117](https://i0.hdslb.com/bfs/album/b8b99e84317db2b8ae410a74e035a62948c1f0df.png)

![image-20210827170041709](https://i0.hdslb.com/bfs/album/0b961e00a299fdb28033b0bc9752cecd56ef2f90.png)

### 1.3.JWT的优势在哪?

![image-20210827170106840](https://i0.hdslb.com/bfs/album/bae21ff76967bc07f8528efe5e87469b988b6e31.png)

### 1.4.JWT具体包含的信息

#### 1.header

![image-20210827170148205](https://i0.hdslb.com/bfs/album/f428ad90644689a1c9f2fcf898081f2589405197.png)

#### 2.Payload

![](https://i0.hdslb.com/bfs/album/0f93ae4f706641f88f7a44e281d4101b0759a7d7.png)

#### 3.Signature

![image-20210827170243910](https://i0.hdslb.com/bfs/album/ca95ea1162f78d165b5a8bfdc26f99a8e94439e6.png)

## 2.SpringBoot JWT 初始化

### 2.1整合POM

```xml
  <dependencies>
        <!--druid-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
            <version>1.2.0</version>
        </dependency>
        <!--mysql-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.38</version>
        </dependency>
        <!--plus-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.4.3</version>
        </dependency>
        <!--jwt-->
        <dependency>
            <groupId>com.auth0</groupId>
            <artifactId>java-jwt</artifactId>
            <version>3.18.1</version>
        </dependency>
        <!-- spring -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>
```

### 2.2测试JWT加密流程

![image-20210827170525494](https://i0.hdslb.com/bfs/album/700373abdc3c3c2c8b96adf5378382969064e7c9.png)

![image-20210827170537381](https://i0.hdslb.com/bfs/album/d97da061803a8ad9f82f4b0f5a5e4df8a532975b.png)

## 3.封装工具类JWTUtils

![image-20210827170611141](https://i0.hdslb.com/bfs/album/b8087ae5ee9d28ca2c4c3bb06b82a87925129c48.png)

## 4.登录接口逻辑

```java
   @GetMapping("/user/login")
    public Map<String, Object> login(User user) {
        HashMap<String, Object> map = new HashMap<>();
        try {
            // find user in DB
            User userDB = userService.login(user);

            HashMap<String, String> payload = new HashMap<>();
            // add info into payload
            payload.put("id", String.valueOf(userDB.getId()));
            payload.put("name", userDB.getName());

            // 生成JWT的令牌
            String token = JWTUtils.getToken(payload);

            // return info to user login
            map.put("state", true);
            map.put("msg", "认证成功");
            map.put("token", token);
        } catch (Exception e) {
            // can't find user
            map.put("state", false);
            map.put("msg", e.getMessage());
        }
        return map;
    }
```

## 5.验证Token逻辑(原始)

```java
 @PostMapping("/user/test")
    public Map<String, Object> test(String token) {
        HashMap<String, Object> map = new HashMap<>();
        /*
        try {
            JWTUtils.verify(token);
            map.put("state", true);
            map.put("msg", "请求成功!");
            return map;

        } catch (SignatureVerificationException e) {
            // 过期异常
            e.printStackTrace();
            map.put("msg", "无效签名!");
        } catch (TokenExpiredException e) {
            // token不一致异常
            e.printStackTrace();
            map.put("msg", "token过期!");
        } catch (AlgorithmMismatchException e) {
            // 算法不一致异常
            e.printStackTrace();
            map.put("msg", "算法不一致!");
        } catch (Exception e) {
            e.printStackTrace();
            map.put("msg", "无效签名!");
        }
             map.put("state", false);
        */
        // 处理自己的业务逻辑
        map.put("state", true);
        map.put("msg", "请求成功");
        return map;
    }
```







## 6.JWT过滤器简化验证Token逻辑

![image-20210827170642222](https://i0.hdslb.com/bfs/album/81df153e620786180fa29883f25d06cc72e5db2d.png)

### 6.1创建JWT登录过滤器

![image-20210827170650576](https://i0.hdslb.com/bfs/album/e43f7cb16b8d19be34a23d52eec09e5a8aaf77b3.png)

### 6.2注册JWT过滤器到Spring容器中

![image-20210827170702967](https://i0.hdslb.com/bfs/album/d2b13be681d2b2644aaaa19193a5a1cbe995ae3b.png)
