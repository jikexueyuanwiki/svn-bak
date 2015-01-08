# Mac OS 10.8 SVN服务器的建立

Mac 10.8开始，不再默认安装svn，需要自行安装

如果安装了XCode，会随同安装svn（AppStore里可直接下载）

**更省事的办法：**

**1. 安装homebrew**

官网链接 [软件](http://brew.sh/index_zh-cn.html)

打开终端Terminal，粘贴下面的命令：

```
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
```

安装过程中，如果出现此警告

```
Warning: Install the "Command Line Tools for Xcode": http://connect.apple.com
```

请打开xcode以后，点击菜单栏的：

```
Xcode -> Preferences… ->  Downloads
```

选中`Command Line Tools for Xcode`，然后安装即可也可以直接去苹果官网下载。

**2. 安装svn**

输入：`brew svn install`

> 安装过程很简单，几乎没有提示
 
**3. 配置svn服务**

1）首先，创建一个svn库的文件夹，如：/svn/repository/

2）在终端输入

```
svnadmin create /svn/repository/
```

这个命令在/svn/repository/文件夹下，创建了需要的文件，然后简单编辑就可以用了

![Image of mac_svn1]
(images/mac_svn1.png)

进入conf文件夹

![Image of mac_svn2]
(images/mac_svn2.png)

首先编辑 svnserve.conf

![Image of mac_svn3]
(images/mac_svn3.png)

保存后，其他两个文件参考里面的内容编辑即可

3）启动

```
svnserve -d -r /svn/repository/
```

结束：kill -9 svnserve

4）测试

可以使用svn命令行，也可以在Windows下用Tortoise SVN测试

地址：svn://192.168.0.1
