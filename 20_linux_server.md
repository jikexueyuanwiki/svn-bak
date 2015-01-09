# 基本的SVN服务器配置

**1. 新建一个目录用于存储SVN所有文件**

```
# mkdir /home/svn
```

**2. 新建一个版本仓库**

```
# svnadmin create /home/svn/project
```

**3. 初始化版本仓库中的目录**

```
# mkdir project project/server project/client project/test (建立临时目录)
# svn import project/ file:///home/svn/project -m "初始化SVN目录"
# rm -rf project (删除临时建立的目录)
```

**4. 添加用户**

要添加SVN用户非常简单，只需在/home/svn/project/conf/passwd文件添加一个形如“username=password"的条目就可以了。		
为了测试，我添加了如下内容:

```
[users]
# harry = harryssecret
# sally = sallyssecret
pm = pm_pw
server_group = server_pw
client_group = client_pw
test_group = test_pw
```

**5. 修改用户访问策略**

/home/svn/project/conf/authz记录用户的访问策略，以下是参考:

```
[groups]
project_p = pm
project_s = server_group
project_c = client_group
project_t = test_group
                        
[project:/]
@project_p = rw
* =
                        
[project:/server]
@project_p = rw
@project_s = rw
* =
                        
[project:/client]
@project_p = rw
@project_c = rw
* =
                        
[project:/doc]
@project_p = rw
@project_s = rw
@project_c = rw
@project_t = rw
* =
```

以上信息表示，只有pm有根目录的读写权，server_group能访问server目录，client_group能访问client目录，所有人都可以访问doc目录.

**6. 修改svnserve.conf文件,让用户和策略配置升效**

svnserve.conf内容如下:

```
[general]
anon-access = none
auth-access = write
password-db = /home/svn/project/conf/passwd
authz-db = /home/svn/project/conf/authz
```

**7. 启动服务器**

```
# svnserve -d -r /home/svn
```

**8. 测试服务器**

```
# svn co svn://192.168.60.10/project
Authentication realm: <svn://192.168.60.10:3690> 92731041-2dae-4c23-97fd-9e1ed7f0d18d
Password for 'root': 
Authentication realm: <svn://192.168.60.10:3690> 92731041-2dae-4c23-97fd-9e1ed7f0d18d
Username: server_group
Password for 'server_group': 
svn: Authorization failed ( server_group没用根目录的访问权 )
```

```
# svn co svn://192.168.60.10/project
Authentication realm: <svn://192.168.60.10:3690> 92731041-2dae-4c23-97fd-9e1ed7f0d18d
Password for 'root': 
Authentication realm: <svn://192.168.60.10:3690> 92731041-2dae-4c23-97fd-9e1ed7f0d18d
Username: pm
Password for 'pm': 
A    project/test
A    project/server
A    project/client
Checked out revision 1.  ( 测试提取成功 )
```

```
# cd project/server
# vim main.c
# svn add main.c 
# svn commit main.c -m "测试一下我的C程序,看什么看,不行啊??"
Adding         main.c
Transmitting file data .
Committed revision 2.  ( 测试提交成功 )
```
