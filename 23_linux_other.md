# 其它常用配置 

## 强制写log脚本

配置pre-commit文件，要求用户每次更新文件都必须写log:

```
# cd /home/svn/project/hooks/
# vim pre-commit
```

文件内容如下:

```
#!/bin/sh
REPOS="$1"
TXN="$2"
SVNLOOK=/usr/bin/svnlook
LOGMSG=`$SVNLOOK log -t "$TXN" "$REPOS" | grep "[a-zA-Z0-9]" | wc -c`
if [ "$LOGMSG" -lt 5(要求的log长度，依实际需要修改) ];
then
echo -e "\nEmpty log message not allowed. Commit aborted!" 1>&2
exit 1
fi
```

> 配置完成后，给本件加上可执行权限。再提交代码时，就必须按要求写注释

## 可修改log脚本

配置pre-revprop-change文件，此文件在show log中修改log时会运行，得到修改的权限，否则会报错:

```
DAV request failed; it's possible that the repository's pre-revprop-change hook either failed or is non-existent. At least one property change failed; repository is unchanged
```

```
# cd /home/svn/project/hooks/
# vim pre-revprop-change
```

文件内容如下:

```
REPOS="$1"
REV="$2"
USER="$3"
PROPNAME="$4"
if ["$PROPNAME" = "svn:log"];then exit 0;fi
exit 1
```

> 配置完后加可执行权限升效。