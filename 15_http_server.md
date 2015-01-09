# 基于http协议的服务端

基于Apache Http Server的Subversion，有以下好处： 

- 能使用WebDAV协议  

- 能使用浏览器作为客户端工具浏览源码仓库。 

- 可以很容易的支持SSPI（Windows域认证）和LDAP，这些都是Apache本身就支持的。 

- 能得到比较完善的Apache安全认证系统，比如SSL加密连接。           

> 目前SVN1.4.6(当前最新版)暂不支持Apache2.2以上版本，请使用Apache2.0版本进行配置。

如果先安装Apache2.0，然后在安装Subversion1.4.6，则Subversion的安装会提示是否配置Apache服务器，选择允许配置。

则以下Apache的配置步骤可以省略。

**1.** 安装Apache服务器    

**2.** 检查Apache的modules目录是否包含`mod_dav_svn.so`以及 `mod_authz_svn.so`，如果没有，从Subversion的bin目录中拷贝这两个文件到modules目录。
> 如果先安装Apache，然后安装Subversion，则会自动拷贝这两个模块。
    
**3.** 在Apache的httpd.conf配置文件中LoadModule位置的最后添加如下两行： 
     
```                   
LoadModule dav_svn_module modules/mod_dav_svn.so    
LoadModule authz_svn_module modules/mod_authz_svn.so  
```   

并且去掉`LoadModule dav_module modules/mod_dav.so`之前的#号


**4.** 如果不执行第2步的拷贝，那么在第3步新添加的两个LoadModule中使用绝对路径；    

**5.** 在httpd.conf配置文件的最后添加以下参数：  

```                   
<Location /svn>
DAV svn  SVN
Path D:\MySVN
AuthType Basic 
AuthName "Subversion repositories"
AuthUserFile D:\MySVN\conf\passwd  
AuthzSVNAccessFile D:\MySVN\conf\authz 
Require valid-user
</Location>
```

其中:  

- `<Location /svn>` 中的svn为浏览器中需要输入的访问地址

- `SVNPath D:\MySVN` 指定svn仓库的物理位置 

- `AuthUserFile D:\MySVN\conf\passwd`  指定svn仓库的密码文件 

- `AuthzSVNAccessFile D:\MySVN\conf\authz` 指定svn仓库的权限设置文件    

**6.** 重启Apache服务器，然后就可以使用http://localhost:8080/svn访问svn仓库。其中8080是Apace服务器设置的端口.