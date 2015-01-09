# 去除 SVN 标志

选中需要取消SVN标记（脱离版本控制）的文件夹（其子文件夹也要取消相应标记）右键选择“TortoiseSVN”的`Export…`项，
          
系统弹出导出路径的信息框，如下图所示：

![Image of export]
(images/export.png)

选定你要导出的路径，若选择E盘则会保存一份干净的文件到E盘。 

选择上图中的`Export unversioned files too`复选框表示将本地不处于版本控制下的文件一起导出。 

也可将每个文件目录下（包括子文件目录下）的.svn文件删除解决此问题。

