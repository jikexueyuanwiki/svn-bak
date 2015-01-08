# 服务器端监视

Subversion是通过Hooks 来控制每次Transaction的行为，有Pre-Commit, Post-Commit 等。

一般情况下我们希望在提交代码后，Subversion可以自动发送邮件给组里的每个成员, 这种情况下可以通过post-commit这个脚本来完成。       

该脚本存放在资源库(Repository)的Hooks目录下，以.tmpl后缀结尾，在Windows平台改成.bat，.cmd或.exe。  

- 当一个Transaction成功完成后，会调用post-commit.exe，并传递如下两个参数，根据这两个参数调用svnlook (Subversion提供的工具) 可以获取相应的信息。  
    
```
set REPOS=%1set REPOS=%1           
set REV=%2set REV=%2
```