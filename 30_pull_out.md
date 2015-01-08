# 迁出配置库内容

**1.** 在本地硬盘上建立一个文件夹“SVN”，并在文件夹“SVN”中建立一个子文件夹（子文件夹为空文件夹），

子文件夹的名称可以根据本公司配置库路径下的对应文件夹名称进行定义。例如在SVN中建立一个test子文件夹。 

**2.** 鼠标选中文件夹“test”右键选择“SVN Checkout…”。

![Image of checkout]
(images/checkout.png)

**3.** 在弹出的窗口中URL of repository栏中输入您要访问的配置库路径，如http:///test（此路径为实验路径，输入时依具体配置库路径而定，可以为根目录的路径也可以为子目录的路径，目录选择要适当）

>  备注：在Revision栏中选择“HEAD revision”项只能获得所输入路径下的最新版本文件。

选择“Revision”项可以输入或选择此路径下的任意历史版本文件。

**4.** 在弹出的窗口Authentication中的Username栏输入用户名，在Password栏输入用户密码，可选择Save authentication复选框保存用户名和密码。