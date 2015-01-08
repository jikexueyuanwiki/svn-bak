# 忽略无需版本控制的文件

在你给配置库中提交内容时，会有一些文件和目录不需要进行版本控制，只需要在你本地硬盘保存即可，这可能包括一些由编译器生成的文件，如`*.obj，*.lst`等。此时可采用添加相应文件到该项目的忽略列表的方法解决。 

选中本地硬盘中无需提交到配置库的文件（此文件在本地硬盘的父目录是处于版本控制下的），右键选择“TortoiseSVN”的`Add to ignore list`项，点击`Add to ignore list`项中的项目.txt.bak代表只忽略这一个文件，若点击`*.bak`代表忽略所有具有`*.bak`后缀的文件。 

如果你同时选择多种文件进行忽略时，就没有子菜单了，仅显示待忽略的个数。