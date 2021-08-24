# Git分布式版本控制工具

## 1.目标

* 了解git基本概念
* 能够概述git的工作流程
* 能够实用git常用命令
* 熟悉代码托管服务
* 能够实用idea操作git

## 2.版本控制的方式

![image-20210820153112299](https://i0.hdslb.com/bfs/album/3a9994c2f34d4f36709c07de34717ec7a93e95d3.png)

### svn

![image-20210820153255843](https://i0.hdslb.com/bfs/album/7c3ffa295fc92369b62c9db252435534941363f8.png)



### git

![image-20210820153308885](https://i0.hdslb.com/bfs/album/3bc3b99eaae613573d3841140750b9ce041decf1.png)

![image-20210820153320747](https://i0.hdslb.com/bfs/album/e81988602d268ae1e71a1267b9e04846ec0a4ef1.png)



## 3.Git工作流程

![image-20210820153357340](https://i0.hdslb.com/bfs/album/790b45e22f8b222ae40852e34092ab6a88485d1d.png)

![image-20210820153456516](https://i0.hdslb.com/bfs/album/1b28f2e2305736963ed5b495161f681b73b379db.png)



## 4.Git安装与常用命令

### 安装

![image-20210820153622325](https://i0.hdslb.com/bfs/album/1d9738e859a382b56b2cc5d84cba5c0b2276e56d.png)

![image-20210820153640836](https://i0.hdslb.com/bfs/album/565304e2b9277846d4aa748a8432d6eb6eeeca3a.png)



### 基本配置等

> 当安装Git后首要做的事是设置用户名称和email地址,因为Git每次提交都会用到用户信息

![image-20210820153748532](https://i0.hdslb.com/bfs/album/ad1e2434d0008c66b698f3c5e6e0537bda98f880.png)



### 获取本地仓库

![image-20210820153919493](https://i0.hdslb.com/bfs/album/3fde0f2d7b6b2182919d90cfbb9cc5c2cbbb0ea5.png)

## 5.基础操作指令

> Git工作目录下丢与文件的修改会存在几个状态

![image-20210820154012595](https://i0.hdslb.com/bfs/album/7d63b823078737250b207a626e034a096029104e.png)



### 查看状态status

![image-20210820154213635](https://i0.hdslb.com/bfs/album/2b518fed00fad37a437d107629594ac636742cde.png)

### 添加工作区到暂存区add

![image-20210820154143314](https://i0.hdslb.com/bfs/album/0e465424562923e53e88de7d3940c9046446cde5.png)

### 提交暂存区到本地仓库commit

![image-20210820154303059](https://i0.hdslb.com/bfs/album/3704c49db2b71512f5d5ec2ed04c77530e8e9ca9.png)

### 查看日志log

![image-20210820154335548](https://i0.hdslb.com/bfs/album/141176893ef15cacd682b58857deb8780d0d9c7c.png)

### 版本回退

![image-20210820154513490](https://i0.hdslb.com/bfs/album/c9b110146a377fc1d3df03a643e68e338cb85d06.png)

### 添加文件至忽略列表

![image-20210820154553125](https://i0.hdslb.com/bfs/album/cb984604da754fea65a4c67a3be718d0622a3228.png)



## 6.分支

### 分支介绍

![image-20210820154829251](https://i0.hdslb.com/bfs/album/8eb74fa9a5becc0cb185daaa453190c004dc3971.png)

![image-20210820154926203](https://i0.hdslb.com/bfs/album/a5c5c6f539bc27dde63a2bb216f0ba24f93532ae.png)



### 分支实用原则和流程



> 几乎所有版本控制系统都以某种形式支持分支,实用分支意味着你恶意把你的工作从开发主线上分离,进行重大Bug的修改,开发新的功能,以免影响开发主线

![image-20210820155058101](https://i0.hdslb.com/bfs/album/1f54bd35d4b6018a4c7365b83fdf9f2632bbb2e9.png)

![image-20210820155143748](https://i0.hdslb.com/bfs/album/bfc1255574e41ac204b69398337cf8170a348c58.png)



## 7.Git远程仓库

### 配置SSH公钥

* 生成SSH公钥
  * ssh-keygen -t rsa
  * 不断回车
    * 如果公钥已经存在,则自动覆盖
* Gitee设置账户公钥
  * 获取公钥
  * ![image-20210820155357876](https://i0.hdslb.com/bfs/album/31d554206eecfe4ed39e2633a429c6126ef0b6c4.png)

* 验证是否配置成功
  * ssh -T git@gitee.com
  * ssh -T git@github.com

## 8.操作远程仓库

### 添加远程仓库

![image-20210820155536291](https://i0.hdslb.com/bfs/album/a51e18503721c76151e5b94b93c78f2149b3ef9a.png)

### 查看远程仓库

![image-20210820155555660](https://i0.hdslb.com/bfs/album/6ee74e1c3d7798c19a27e110e695ad4df37af436.png)

### 推送到远程仓库

![image-20210820155618379](https://i0.hdslb.com/bfs/album/6edbfab99c10b16ac89f4b0a4bbe2efa9acd8868.png)

![image-20210820155701139](https://i0.hdslb.com/bfs/album/4b61c6dbe0fa98410fcae0b9cf08eccc5d9364c9.png)

### 本地分支与远程分支的关联关系

![image-20210820155811491](https://i0.hdslb.com/bfs/album/6a8daf42cf56759b9700baa7b823c9bccdffa2db.png)

### 从远程仓库克隆

![image-20210820155829435](https://i0.hdslb.com/bfs/album/faff0e5d7f777a2e42519f8d0bd70f0218274767.png)

### 从远程仓库中抓取和拉取

![image-20210820155912011](https://i0.hdslb.com/bfs/album/418910165f8d7e6e990e1495a0d8fdd6c478fd03.png)

![image-20210820155917714](https://i0.hdslb.com/bfs/album/7e2096f6bdcd0ccb7ba034b75fb8f268560f0c3d.png)

![image-20210820160022148](https://i0.hdslb.com/bfs/album/81b296715330cdcb7b8b70e7d1fe96fd82f3b666.png)



### 解决合并冲突

![image-20210820160047586](https://i0.hdslb.com/bfs/album/8d050a983ffc4050b9c742c03a217a45814f353e.png)

![image-20210820160101450](https://i0.hdslb.com/bfs/album/68f44bbf476482c2683c5d374ff73696bf07b195.png)

![image-20210820160139066](https://i0.hdslb.com/bfs/album/3bfd92c44c905df12cfc5e23424e1045f4d9a84b.png)

## 9.idea中使用Git

### idea配置git

![image-20210820160247405](https://i0.hdslb.com/bfs/album/b12ba943b11d9715c7aea366f8e28488df0f32d6.png)

### 初始化本地仓库

![image-20210820160323667](https://i0.hdslb.com/bfs/album/04a79da546ccd22662452efdbb131b14177d889e.png)

### 设置远程仓库

![image-20210820160338770](https://i0.hdslb.com/bfs/album/7989c66ab84f16f65d966b76d3e636f7b384738e.png)

### 提交到本地仓库

![image-20210820160357811](https://i0.hdslb.com/bfs/album/c6f8631bf7ac7b6834693d75eaa5187e6f92b1ca.png)

### 推送到远程仓库

![image-20210820160413738](https://i0.hdslb.com/bfs/album/f427f3549865dafbb327dbb0b5d7f7fb987863a5.png)

### 克隆仓库到本地

![image-20210820160426802](https://i0.hdslb.com/bfs/album/eb636b12a9facfcc3ee12880e3cde57f79177b11.png)

### 创建分支

![image-20210820160450059](https://i0.hdslb.com/bfs/album/a7847a556a3cd9d84c1acdd652818e8f2da52651.png)

### 切换分支

![image-20210820160502153](https://i0.hdslb.com/bfs/album/61633ed528fdf7b32fcf61e847d546f34e39c040.png)

### 解决冲突

![image-20210820160538516](https://i0.hdslb.com/bfs/album/44592d43de6167338b0b96410c1d3f5b3d877082.png)



### IDEA常用Git操作图解

![image-20210820160619313](https://i0.hdslb.com/bfs/album/e736a0f9db0e7499932bd03474a4bc20a5132f8d.png)



## 10.团队开发场景

1. 由组长(项目经理),基于项目创建本地仓库;创建远程仓库,推送项目到远程仓库

   ![image-20210820160817673](https://i0.hdslb.com/bfs/album/2f1dc6cf701899a207781927c72de9ad1b010baa.png)

2. 每一位组员从远程仓库克隆项目到IDEA中,每个人拥有一个副本,开始正式开发

   ![image-20210820160902953](https://i0.hdslb.com/bfs/album/61ffe88b1a4e540e7a535c4a2d5a5d82d5a2807a.png)

3. 组员A修改工作区,提交到本地仓库,再推送到远程仓库,组员B直接从远程获取最新的代码

   ![image-20210820160942937](https://i0.hdslb.com/bfs/album/4faef50f78b078d7f0a230786567549a67b557b2.png)

4. 组员A和组员B修改了同一文件的同一行,提交到本地没有问题,但是推送到远程时,后一个操作的推送失败

   解决方法:需要先获取远程仓库代码到本地,编辑冲突,提交并推送代码

   ![image-20210820161110722](https://i0.hdslb.com/bfs/album/343f27e5536eef5577c5a7914652e5880f37473d.png)

# 注意点

1. **切换分支前必须先提交本地修改**



# 问题

1.版本回退后,如何向回退之前的版本回退



2.两个不想关的仓库向一个远程仓库发送会出现问题 不允许合并相关问题

## 解决

出现这个问题的最主要原因还是在于本地仓库和远程仓库实际上是独立的两个仓库。假如我之前是直接clone的方式在本地建立起远程github仓库的克隆本地仓库就不会有这问题了。

```
git pull origin master --allow-unrelated-histories
```

3.idea中pull代码,怎么看哪些代码是pull过来的,不是自己写的