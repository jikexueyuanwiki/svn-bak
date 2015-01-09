# Ignore 指定忽略文件或目录

AndroidStudio 的 Setting 面板中配置的 ignore 似乎没什么效果，

下面先看看忽略掉的目录的显示效果（比较暗的黄绿颜色）

![Image of setting]
(images/setting.png)

- 在 Setting 中的配置，主要忽略的目录和文件：		
系统默认有两三个文件和目录，自己添加的 .gradle .idea build 目录

![Image of setting2]
(images/setting2.png)

- 通过 TortoiseSVN 来添加忽略：

![Image of setting3]
(images/setting3.png)

- 对于更新和提交：向上的绿色是commit ，向下的蓝色 是 update

![Image of setting4]
(images/setting4.png)

> 如果遇到 ignore 或其他设置无效等意外情况，可以尝试重启 androidstudio 或执行下 svn 的 update 试试







