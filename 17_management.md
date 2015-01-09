# SVN权限管理

实例：

XXX公司是一家电子元器件设备供应商，其中有个ARM部门，专门负责ARM芯片的方案设计、销售，并在北京、上海各设立了一个办事处。

对于工作日志，原先采用邮件方式发给经理，但是这种方式有个缺点，那就是不具备连续性，要看以前的日志必须一封一封邮件去查看，很麻烦。 

于是就想到利用Subversion， 让员工在自己电脑上编辑日志，然后利用svn传送回来，既方便员工自己编写日志，又方便对日志的归档处理，

而且提交日志的时候只需要执行一下 svn commit 即可，比发送邮件还要简单的多。  

部门文档的目录结构如下部门文档的目录结构如下：
  
```          
test            
├─diary                   
│  ├─headquarters          
│  ├─beijing              
│  └─shanghai              
├─ref                      
└─temp                 
```

- **test：**部门名称 

- **diary：**工作日志目录

- **headquarters：**总部工作日志目录

- **beijing：**北京办日志目录

- **hanghai：**上海办日志目录

- **ref：**公司公共文件参考目录

- **temp：**临时文件目录

## 人员情况    

- morson，公司总经理，不习惯使用电脑，更喜欢传统的纸与笔，以及面对面的交流   

- michael，arm事业部的部门经理，没事的时候喜欢弄点儿新技术，用svn来管理日志，就是他想出来的主意   

- scofield，北京办人员，老员工，为人油滑难管  

- lincon，上海办人员，老员工，大老实人一个   

- linda，总部协调员、秘书，文笔不错，长得也不错  

- rory，单片机技术员，技术支持

## 访问权限需求分析

- 允许总经理、部门经理读取所有文件。顺便给他们开放写权限，以便体现对他们职位的尊重，虽然对于某些文件来说，他们若拥有“写”权限其实也没什么用处  

- 除部门经理外，所有其他人员，均只能看到本办事处人员工作日志  

- 不允许匿名访问    - ref目录只允许经理和秘书读写，对其他人只读  

- temp目录人人都可以随意读写  

**在服务器端d:\svndata\test\conf配置svnserve.con**

```
[general]     
password-db = passwd.conf    
anon-access = none    
auth-access = write    
authz-db = authz.conf
```

**在服务器端d:\svndata\test\conf配置passwd.conf进行用户创建**
         
```
[users]     
morson = ShowMeTheMoney    
michael = mysecretpassword    
scofield = hellolittilekiller    
lincon = asyouknows111    
rory = 8809117     
linda = IlikeWorldCup2006
```

**在服务器端d:\svndata\test\conf配置authz.conf进行用户创建**

> 注意：在权限设置中在权限设置中，用户名必须顶格，不能留有空格不能留有空格！

```              
[groups]  
g_vip = morson 
g_manager = michael
g_beijing = scofield
g_shanghai = lincon 
g_headquarters = rory, linda
g_docs = linda 

[/] 
@g_manager = rw
* = r

[/diary/headquarters]
@g_manager = rw 
@g_headquarters = rw
@g_vip = r
* =  

[/diary/beijing]
@g_manager = rw
@g_beijing = rw
@g_vip = r
* =  

[/diary/shanghai]
@g_manager = rw
@g_shanghai = rw
@g_vip = r
* =  

[/ref] 
@g_manager = rw
@g_docs = rw
* = r  

[/temp]
* = rw
```

这样SVN的配置权限设置完毕。
