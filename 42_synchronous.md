# 获取历史文件

- 查看历史文件		
鼠标选中文件夹test右键选择“TortoiseSVN”的`Show log`项，系统弹出此路径下的所有文件版本信息，如下图所示：

![Image of look]
(images/look.png)

此时也可双击文件查看修改的内容（比较上一版本所修改的内容）。

- 获取历史文件		
鼠标选中文件夹右键选择“TortoiseSVN”的“update item to revision ”项，后系统提示需要选择下载的版本，如下图所示：

![Image of get]
(images/get.png)

操作完成后，再去看看document文件，是不是内容都没了，通过这样的方法，我们可以在版本历史中任意回溯。

- 版本同步		
作为一个支持并行开发的配置管理工具，我们如何获得别人修改的内容，这里我们使用update命令。		
我们在需要同步的目录上点击鼠标右键点击update，我们即可获得服务器上最新内容的同步。

![Image of synchronous]
(images/synchronous.png)


