# Seeworld
As a human different between ZHAO.
apt-get update
apt-get install update
apt-get install python-software-properties -y
add-apt-repositort ppa:dlundquist/sniproxy #添加PPA源
ENTER #回车键

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.3EkZK0n4ya 
--trustdb-name /etc/apt//trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg 
--keyring /etc/apt/trusted.gpg.d//debian-archive-jessie-stable.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-squeeze-automatic.gpg 
--keyring /etc/apt/trusted.gpg.d//debian-archive-squeeze-stable.gpg --keyring /etc/apt/trusted.gpg.d//debian-archive-wheezy-automatic.gpg 
--keyring /etc/apt/trusted.gpg.d//debian-archive-wheezy-stable.gpg --keyserver hkp://keyserver.ubuntu.com:80/
--recv C90AE60C838E76DB2871E82FBB887E85ED122FA0
gpg: requesting key ED122FA0 from hkp server keyserver.ubuntu.com
gpg: key ED122FA0: public key "Launchpad PPA for Dustin Lundquist" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
apt-get update #再次更新
apt-get install sniproxy -y #安装sniproxy
vi /etc/sniproxy.conf
然后我们编辑配置文件,这次只说一下,我设置的为泛域名模式,所有的访问都通过sni访问
user deamon
pidfile /var/run/sniproxy.pid

listen 443 {
        proto tls
        table https_hosts
        access_log {
                filename
/var/log/sniproxy/https_access.log     #日志目录
                    priority notice
            }
}

table https_hosts {
        .* *:443
}

命令:
sniproxy #启动
service sniproxy stop #停止
