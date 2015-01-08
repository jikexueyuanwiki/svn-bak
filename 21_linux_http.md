# 配置SVN服务器的HTTP支持

## 转换SVN服务器的密码


由于SVN服务器的密码是明文的，HTTP服务器不与支持，所以需要转换成HTTP支持的格式。用一个Perl脚本完成这个工作.

脚本内容如下:

```
# cd /home/svn/project/conf/
# cat PtoWP.pl 
#!/usr/bin/perl
# write by huabo, 2009-11-20
               
use warnings;
use strict;
                
#open the svn passwd file
open (FILE, "passwd") or die ("Cannot open the passwd file!!!\n");
                
#clear the apache passwd file
open (OUT_FILE, ">webpasswd") or die ("Cannot open the webpasswd file!!!\n");
close (OUT_FILE);
                
#begin
foreach (<FILE>) {
   if($_ =~ m/^[^#].*=/) {
   $_ =~ s/=//;
   `htpasswd -b webpasswd $_`;
	}
}

# ./PtoWP.pl ( 先给该脚本加可执行权限，然后执行以转换密码 )
Adding password for user pm
Adding password for user server_group
Adding password for user client_group
Adding password for user test_group
现在目录下会多一个webpasswd文件。
```

## 修改httpd.conf，添加关于SVN服务器的内容


编辑/etc/httpd/conf/httpd.conf，在最后添加如下信息:

```
<Location /project>
  DAV svn
  SVNPath /home/svn/project/
  AuthType Basic
  AuthName "svn for project" 
  AuthUserFile /home/svn/project/conf/webpasswd 
  AuthzSVNAccessFile /home/svn/project/conf/authz
  Satisfy all
  Require valid-user
</Location>
```

## 启动HTTPD服务器


```
# service httpd restart
Stopping httpd:   [FAILED]                                       
Starting httpd:   [  OK  ] 
```                                       

