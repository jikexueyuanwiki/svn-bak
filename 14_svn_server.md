# 基于svn协议的服务端


**1.** 安装Subversion后，使用命令 svnadmin create "D:\MySVN" 创建svn资源库，资源库地址为D:\MySVN   

**2.** 打开 D:\MySVN\conf\svnserve.conf，去掉以下内容之前的注释符 
              
```
[general]        
anon-access = none       
auth-access = write       
password-db = passwd        
realm = My First Repository
```

> 说明： 		
	anon-access = none     不允许匿名访问！         
	auth-access = write    允许提交修改                 
	password-db = passwd   密码文件名字
	
如果
		
```
[general]           
anon-access = read  → anon-access = none
```

**3.** 用记事本打开D:\MySVN\conf\passwd，添加用户名(user)和密码(passwd) 
              
```
[users]         
user=password         
```

可以添加多个这样的用户名密码对。   

**4.** 创建svn服务，并启动，这样svn就会开机自动启动  

在控制台下，输入如下命令：

```             
sc create svnservice binpath= "\"D:\program 
 files\Subversion\bin\svnserve.exe\" --service –r D:\MySVN” displayname= SVNService" depend= Tcpip
```

> 注意：               

a. 如果路径中包括空格，一定要用“\”处理“"”号，        
   例如svnserve.exe在c:\program files\subversion\中，则命令应该写为：		
   binpath= \"c:\program files\subversion\bin\svnserve.exe\"     
            
b. sc对选项的格式还有要求，所有的“=”前不能有空格，而后面必须有空格。		
   例如depend= Tcpip不能写为depend = Tcpip或depend=Tcpip    

**5.** 经过上述四步的操作，就可以使用svn://localhost访问SVN服务器。