# SVN密码管理

SVN使用svn协议以及http协议的密码处理是有所不同的，svn使用明文，http则可以可以使用md5加密，对应于conf/passwd文件，两者的形式也不同。  

- **基于svn协议的passwd文件**

```
[users] 
Larry = larry
```

在conf/passwd文件中增加用户名和密码对就可以。   

- **基于http协议的passwd文件**(缺少[users]头，用户名和密码的分隔为分号)：

```
larry1:$apr1$9i......$46q2xMws37UiwyL1w8MkN
```

* 可以通过手动编辑的方式增加用户名和密码(可以是明文)

* 使用Apache的htpasswd工具创建用户 
     
创建第一个用户 `htpasswd -cm d:\Mysvn\conf\passwd user1` 
  
回车后会要求输入密码     

创建第二个用户 `htpasswd -m d:\Mysvn\conf\passwd user1`