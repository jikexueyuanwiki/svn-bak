# 增加文件

首先新建目录：		
我们在工作目录中新建一个目录，例如document

我们有2种方式来添加目录：

**1. 打开菜单选择add功能**

![Image of add]
(images/add.png)

在弹出的add窗口中会列出所有待添加的文件和目录

![Image of document]
(images/document.png)

我们这里只需要点击ok即可，如果有不需要添加的内容，将其勾除 添加成功后我们可以看到

![Image of three]
(images/three.png)

该目录的图标从通用的文件夹变为带红色惊叹号的文件夹，注意这个时候我们并没有把该目录添加到服务器上，只是在本地做了一个添加的标记而已，然后我们使用commit操作完成 

![Image of three2]
(images/three2.png)

在打开的提交操作窗口，这里列出了需要操作的对象和状态，输入提交信息

![Image of commit]
(images/commit.png)

确认后，document目录被添加至服务器上

![Image of path]
(images/path.png)

再次强调SVN的revision是针对操作的，每一次操作revision加1

现在我们的document目录也变成绿色小勾的正常状态了
               
![Image of green]
(images/green.png)

**2. 直接打开菜单选择commit功能**

TortoiseSVN支持这样的快捷操作，你可以直接选择commit，客户端会帮助你检查有哪些变动，例如我们再添加一个Tools目录，直接选择commit。

在弹出的commit窗口中，我们可以看到tools目录是一个non-versioned的状态，我们选择这个目录，并且添加Message，确定 。

![Image of tools1]
(images/tools1.png)

同样可以完成将tools添加到服务器上的操作 

![Image of tools2]
(images/tools2.png)

- **新建文件：**		
对于SVN来说文件和目录是同一种性质的内容，所以文件的添加方式和目录完全相同我们这里就不详细介绍了，我们新建一个readme.txt的空文件到document目录下，然后在该目录中点击commit，确认后该文件被添加到服务器上		

![Image of tools3]
(images/tools3.png)