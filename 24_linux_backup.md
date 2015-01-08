# 备份管理

svn服务器的定期备份是很重要的，最简单的方式是定时备份仓库目录。

**1. 新建备份目录**

```
# mkdir /opt/project_backup
```

**2. 编写备份脚本**

```
# cd /home/svn/
# vim project_backup.sh
```

内容如下:

```
#!/bin/bash
#write by huabo, 2009-11-20
```

```                
cd /home/svn
now=`/bin/date +%Y%m%d`
/bin/tar czvf "project_backup_$now.tar.gz" project/ && rm -rf /opt/project_backup/* && /bin/mv project_backup_*.tar.gz /opt/project_backup/
if [ $? == 0 ]
then
  result="OK!!"
else
  result="False!!"
fi
```

```                
#send mail to administrator
/bin/mail caodaijun@pica.com -s "project_backup_$now" <<MESSAGE
Result: `/bin/echo $result`
MESSAGE
```

> 给该脚本添加可执行权限。