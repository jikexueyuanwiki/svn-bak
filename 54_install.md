# 安装 SVN 插件
          
以Eclipse3.4.2为例，不同版本的Eclipse对应不同版本的SVN插件。

方法一：直接上网下载

[SVN官网](http://subclipse.tigris.org/servlets/ProjectProcess?pageID=p4wYuA)		

分别放入Eclipse的plugins和feature目录中 

方法二：直接解压到 Eclipse 安装目录
          
**1.** 打开eclipse，在菜单栏中选择Help→Software Updates→Find and Install；  

**2.** 选择Search for new features to install，点击Next进入下一步；  

**3.** 点击“New Remote Site”按钮，在弹出的对话框中输入：

```
name：svn   url：http://subclipse.tigris.org/update_1.4.x
```

点击OK，关闭对话框，并点击Finish按钮，eclipse自动下载插件安装程序；  

**4.** 下载完插件之后，进入安装画面。  

**5.** 选择所要安装的SVN插件内容，这里去掉第二个选项Subclipse Integrations，点击下一步；  

**6.** 选择 “I accept the terms in the license agreements”并点击Next，直到点击Finish即可，进入下一步。  

**7.** 开始安装SVN插件，安装完成之后，重启eclipse。