# 配置邮件提醒支持

## 安装Perl模块Module::Build

```
# wget http://search.cpan.org/CPAN/authors/id/D/DA/DAGOLDEN/Module-Build-0.36_11.tar.gz
# tar xvf Module-Build-0.36_11.tar.gz 
# cd Module-Build-0.36_11
# perl Build.PL 
# ./Build 
# ./Build test
# ./Build install
# cd ..
```

## 安装Perl模块Authen::SASL

```
# wget http://search.cpan.org/CPAN/authors/id/G/GB/GBARR/Authen-SASL-2.15.tar.gz
# tar xvf Authen-SASL-2.15.tar.gz 
# cd Authen-SASL-2.15
# perl Makefile.PL 
# make test
# make install# cd ..
```

## 安装Perl模块Net::SMTP_auth

```
# wget http://search.cpan.org/CPAN/authors/id/A/AP/APLEINER/Net-SMTP_auth-0.08.tar.gz
# tar xvf Net-SMTP_auth-0.08.tar.gz 
# cd Net-SMTP_auth-0.08
# perl Makefile.PL 
# make test
# make install
# cd ..
```

## 安装Perl模块SVN::Notify

```
# wget http://search.cpan.org/CPAN/authors/id/D/DW/DWHEELER/SVN-Notify-2.80.tar.gz
# tar xvf SVN-Notify-2.80.tar.gz 
# cd SVN-Notify-2.80
# perl Build.PL 
# ./Build 
# ./Build test
# ./Build install
# cd ..
```

## 启动邮件服务器

```
# service sendmail restart
Shutting down sendmail: [FAILED]                                  
Starting sendmail:      [  OK  ]                                        
Starting sm-client:     [  OK  ]                                       
```

## 配置自动发邮件脚本

修改post-commit脚本,以支持邮件通知功能：

```
# cd /home/svn/project/hooks/
# vim post-commit
```

内容如下:

```
#!/bin/sh
REPOS="$1"
REV="$2"
```

```              
/usr/bin/svnnotify --repos-path "$1" --revision "$2" --to caodaijun@pica.com --from caodaijun@feinno.com --handler "HTML::ColorDiff"  --with-diff --smtp localhost --smtp-user root --smtp-pass 5201314318 -c "UTF-8" -g zh_CN -o raw --svnlook /usr/bin/svnlook --subject-prefix '[SVN Update]'
```

- to参数代表接收邮件的地址，可以有多个；

- from参数是虚拟的，代表你的发送地址，一般情况下，这个参数 不重要，但如果接收者的邮件服务器有反垃圾邮件的功能，需要判定源地址的话，这个参数是否合法就显得很重要了。

再给该脚本添加可执行权限：

```
# chmod +x post-commit
```

> 再次提交时，就会给指定邮件地址发信了。