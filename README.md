# 安装ftp

1、检查安装

_rpm -q vsftpd_

2、下载vsftpd vsftpd-2.2.2-21.el6.x86\_64.rpm

3、安装

_rpm -ivh vsftpd-2.2.2-21.el6.x86\_64.rpm_

4、添加用户和组

_groupadd ftp_

_useradd -d /home/ftpcredit -g ftp -s /sbin/nologin ftpcredit_

_passwd ftpcredit_

5、配置防火墙

关闭或者允许访问21端口

_/sbin/iptables -I INPUT -p tcp --dport 21 -j ACCEPT_

_/etc/rc.d/init.d/iptables save _

_/etc/init.d/iptables restart_

6、重启vsftpd

_service vsftpd start_

### 可能出现的问题：

1、500 OOPS  xxx /home/\*无法访问、拒绝访问

解放方法：

_getenforce_

_setenforce 0_

_vim /etc/selinux/config_

_将selinux=enforcing或permissive改成disabled_

