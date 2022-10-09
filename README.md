
##### This Kernel is compiled based on [Netflix/TCPLOG_DUMPER](https://github.com/Netflix/tcplog_dumper) project, and can be replaced directly on FreeBSD 13.1-Release AMD64.


#### Prerequisite
     FreeBSD version 13.1 amd64
     
     
#### USAGE

1. Change Kernel
```
tar -zxvf freebsd-13.1_bbr_kernel.tar.gz -C /root/
mv /boot/kernel /boot/kernel.old
cp -R /root/kernel /boot/
```

2. Enable BBR
```
sysrc kld_list+="tcp_rack tcp_bbr"
echo 'net.inet.tcp.functions_default=bbr' >> /etc/sysctl.conf
echo 'net.inet.tcp.bb.log_auto_mode=4'  >>/etc/sysctl.conf
echo 'net.inet.tcp.bb.log_auto_all=1' >>/etc/sysctl.conf
echo 'net.inet.tcp.bb.log_auto_ratio=1' >>/etc/sysctl.conf
```

3. Reboot and Check
```
user@:~ $ reboot


user@:~ $ sysctl net.inet.tcp.functions_default
net.inet.tcp.functions_default: bbr
```
