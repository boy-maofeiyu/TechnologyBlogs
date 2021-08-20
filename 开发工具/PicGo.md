# PicGo

# 问题?

       最近突发奇想,想要写技术博客来巩固自己的知识,以备以后在工作中能够直接复制粘贴,一直使用Typora作为编辑器的我,遇到了一个棘手的问题,Typora图片常规存储在assets目录下,而大多数博客网站无法上传多文件,且不支持zip,rar等压缩包格式,因此我选择了免费图床通过OSS存储来替代我本地的图片资源. 一开始我选择了手动上传的方式,但是随着图片的增多,一张一张图片上传不仅慢,而且效率极低,手动上传几十张图片真是让我崩溃,于是我就开始联想有没有自动上传的方法,我发现了PicGo+Typora实现图床自动,大大提高了我撰写开发文档和发表个人博客的效率.

![](https://i0.hdslb.com/bfs/album/cd94c80d405d8642cb172fa0fec1de6cfc06cc33.jpg)

# 1. 三个实用稳定免费的图床

[https://www.hualigs.cn/](https://www.hualigs.cn/)

[https://sm.ms/login](https://sm.ms/login)

[https://imgtu.com/album/yfVZn](https://imgtu.com/album/yfVZn)


# 2. 开发文档

> 开发文档


[https://picgo.github.io/PicGo-Doc/zh/guide/config.html](https://picgo.github.io/PicGo-Doc/zh/guide/config.html)


> API开发文档


[https://picgo.github.io/PicGo-Core-Doc/](https://picgo.github.io/PicGo-Core-Doc/)


> 自主构建PicGo(Vue跨平台)


[https://molunerfinn.com/tags/Electron-vue/](https://molunerfinn.com/tags/Electron-vue/)

# 3.下载地址

[https://github.com/Molunerfinn/PicGo/releases](https://github.com/Molunerfinn/PicGo/releases)

# 4. 应用概述

## 4.1 PicGo是什么?

> 一个用于快速上传图片并获取图片` URL 链接的工具`


## 4.2 兼容性`可自研`

PicGo 本体支持如下图床：
*   `七牛图床` v1.0
*   `腾讯云 COS v4\v5 版本` v1.1 & v1.5.0
*   `又拍云` v1.2.0
*   `GitHub` v1.5.0
*   `SM.MS V2` v2.3.0-beta.0
*   `阿里云 OSS` v1.6.0
*   `Imgur` v1.6.0


# 5. 功能介绍

- 支持`拖拽图片`上传

- 支持`快捷键上传`剪贴板里第一张图片

- Windows 和 macOS 支持右键图片文件通过`菜单上传` (v2.1.0+)

- 上传图片后`自动复制链接`到剪贴板

- 支持`自定义`复制到剪贴板的`链接格式`

-   支持修改`快捷键`，默认快速上传快捷键：

&ensp;&ensp;&ensp;&ensp;`command+shift+p`（macOS）

&ensp;&ensp;&ensp;&ensp; `control+shift+p`（Windows\Linux)

- 支持`插件扩展`开发

- 支持通过发送 `HTTP 请求`调用 PicGo 上传（v2.2.0+)


# 6. 快速上手

> 注意:确保安装了node.js≥8



## 6.1顶部栏上传提示

> 顶部栏上传只支持macOS系统。



1.  可以直接拖拽图片到顶部栏PicGo图标处上传。
2.  可以将图片复制到剪贴板，然后点击顶部栏PicGo图标，点击`等待上传`区的图片，就会自动上传了。

![fVEf5d.gif](https://z3.ax1x.com/2021/08/05/fVEf5d.gif)

## 6.2 主窗口上传

> 在Mini窗口或者macOS的顶部栏图标处右键 -> 打开`详细窗口`，即可打开主窗口。



![fVERVe.md.png](https://z3.ax1x.com/2021/08/05/fVERVe.md.png)

1.  直接在主窗口上传区域拖拽图片上传。
2.  直接在主窗口上传区域点击，然后弹出文件浏览器后选择图片上传。
3.  可以将图片复制到剪贴板，然后点击`剪贴板图片上传`按钮来上传。


# 7. 配置手册

PicGo的配置文件在不同系统里是不一样的。
*   Windows: `%APPDATA%\picgo\data.json<br />`*   Linux: `$XDG_CONFIG_HOME/picgo/data.json` or `~/.config/picgo/data.json<br />`*   macOS: `~/Library/Application\ Support/picgo/data.json<br />`举例，在windows里你可以在：
`C:\Users\你的用户名\AppData\Roaming\picgo\data.json`找到它。
在linux里你可以在：
`~/.config/picgo/data.json`里找到它。
macOS同理。


## 7.1 常见图床配置

> 更多配置见官方手册


[https://picgo.github.io/PicGo-Doc/zh/guide/config.html#imgur图床](https://picgo.github.io/PicGo-Doc/zh/guide/config.html#imgur%E5%9B%BE%E5%BA%8A)


### 7.1.1 SMMS图床

配置项及说明：

```XML
{
  "token": "" // 通过SMMS后台获取的api token值
}
```


注册并登录[smms](https://sm.ms/home/apitoken)后台获取token值。

![](https://i.loli.net/2021/08/05/KAS1iDZaehWjuX2.png)


### 7.1.2 GitHub图床

```XML
{
  "repo": "ossimages", // 仓库名，格式是username/reponame

  "token": "", // github token

  "path": "img/", // 自定义存储路径，比如img/

  "customUrl": "https://boy-maofeiyu.github.io/ossimages/", // 自定义域名，注意要加http://或者https://

  "branch": "master" // 分支名，默认是main

}

```


**1.**  注册Github

**2.**  新建一个仓库,记下你取的`仓库名`。

**3.**  `生成一个token`用于PicGo操作你的仓库：

访问：[https://github.com/settings/tokens](https://github.com/settings/tokens)

然后点击`Generate new token`。

把`repo的勾打上`即可。然后翻到页面最底部，点击`Generate token`的绿色按钮生成token。

**注意:** 这个token生成后只会显示一次！你要把这个token复制一下存到其他地方以备以后要用。



**注意:** 仓库名的格式是用户名/仓库，比如我创建了一个叫做test的仓库，在PicGo里我要设定的仓库名就是Molunerfinn/test。一般我们选择main分支即可。然后记得点击确定以生效，然后可以点击设为默认图床来确保上传的图床是GitHub。

至此配置完毕，已经可以使用了。当你上传的时候，你会发现你的仓库里也会增加新的图片了：


### 7.1.3阿里云OSS

配置项及说明：

```XML
{

  "accessKeyId": "",

  "accessKeySecret": "",

  "bucket": "", // 存储空间名

  "area": "", // 存储区域代号

  "path": "", // 自定义存储路径

  "customUrl": "" // 自定义域名，注意要加http://或者https://

}
```


首先先在阿里云OSS的[控制台](https://usercenter.console.aliyun.com/#/manage/ak)里找到你的`accessKeyId`和`accessKeySecret`： 

创建一个`bucket`后，存储空间名即为`bucket`:

确认你的[存储区域](https://www.alibabacloud.com/help/zh/doc-detail/31837.htm?spm=a2c63.p38356.a3.3.179112f0PBtYui)的代码：

也可以在bucket页面找到：

存储路径比如`img/`的话，上传的图片会默认放在OSS的`img`文件夹下。注意存储路径一定要以`/`结尾！存储路径是可选的，如果不需要请留空。

如上图，存储区域就是`oss-cn-beijing`

存储路径比如`img/`的话，上传的图片会默认放在OSS的`img`文件夹下。注意存储路径一定要以`/`结尾！存储路径是可选的，如果不需要请留空。


# 8. PicGo设置

## 8.1 设置日志文件

你可以在这个设置里面打开日志文件查看，也可以设置输出的日志类型（比如成功、失败或者不输出等）。

![](https://i.loli.net/2021/08/05/BEDLrCaYJtx1Fi8.png)


## 8.2 自定义快捷键

会打开快捷键面板（v2.2.0+），可以选择禁用或者启用快捷键：

![](https://i.loli.net/2021/08/05/7wgZBXIvDpiH1dK.png)


## 8.3 自定义链接格式

PicGo预置的有四种链接格式：`MarkdownHTML` \ `URL` \ `UBB`

如果你都不喜欢，想要自定义链接格式，可以选择`Custom`，然后在PicGo设置里点击`自定义链接格式`，然后你可以配置自己想要的复制的链接格式。


## 8.4 自动时间戳命名

![](https://i.loli.net/2021/08/05/8nhoKrJZa3HxN1e.png)

开启之后会自动将上传的文件名替换成时间戳：


## 8.5 PicGo-Server设置 

2.2版本之后，PicGo内部会默认开启一个小型的服务器，用于配合其他应用来调用PicGo进行上传。监听的地址推荐就默认的 `127.0.0.1` （本机），端口推荐默认的 `36677`。当然如果你不想要开启也可以选择关闭，只不过推荐你可以开启~可以配合一些第三方工具实现很方便的上传工作流。

[https://picgo.github.io/PicGo-Doc/zh/guide/advance.html#http调用上传剪贴板图片](https://picgo.github.io/PicGo-Doc/zh/guide/advance.html#http%E8%B0%83%E7%94%A8%E4%B8%8A%E4%BC%A0%E5%89%AA%E8%B4%B4%E6%9D%BF%E5%9B%BE%E7%89%87)


# 9. 插件安装

## 9.1 b站插件

![](https://i.loli.net/2021/08/05/w5jnZgB2YWt7x6l.png)

### 9.1.1 获取SESSDATA

1.  登录[B站](https://www.bilibili.com/)

2.  按`F12`打开控制台

3.  找到`SESSDATA`复制即可


![](https://i0.hdslb.com/bfs/album/bd64f2f8459a8701a88191568683d9f6520be627.png)



# 10. Typora+PicGo解放生产力

## 10.1 Typora配置文档

Typora插入图片配置

[https://support.typora.io/Images/#when-insert-images](https://support.typora.io/Images/#when-insert-images)


Typora上传服务配置

[https://support.typora.io/Upload-Image/](https://support.typora.io/Upload-Image/)


![](https://i0.hdslb.com/bfs/album/2e29dcfda1b70f74397a8e372a3ab30cf75dc455.png)

![](https://i0.hdslb.com/bfs/album/13fbfdd06f07b8487829d55d901158fa25beab2f.png)

## 10.2 插入图片时自动上传


1. 用户可以告诉 Typora 在插入时`自动上传图像`（包括从菜单、Touch Bar、通过复制粘贴或拖放插入图像）。

2. 要启用此功能，请在“插入时...”选项下选择“上传图像”，如下面的屏幕截图所示。
然后，如果您希望“自动上传”仅适用于本地图片，请只勾选`Apply above rules to local images`，

3. 如果您还想重新上传已经托管在远程网站上的图片，您也可以勾选`Apply above rules to online images`。

![](https://i0.hdslb.com/bfs/album/dcd9e600c0968cef5b48b98bd2e1b757f4772f33.png)


## 10.3 手动上传

### 10.3.1 上传图片

您可以右键单击图像，然后单击“上传图像”以使用首选项面板中配置的应用程序上传所选图像。

### 10.3.2 上传所有本地图片

如果您的 Markdown 文件包含大量本地图片，并且您想一键上传所有图片，您可以单击菜单 → `Format`→ `Image`→`Upload All Local Images`上传所有本地图片。

