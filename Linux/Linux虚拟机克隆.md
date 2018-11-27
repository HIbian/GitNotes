# Linux虚拟机克隆

## 修改主机名

`vi /etc/sysconfig/network`

修改host名

## 修改IP地址

`vi  /etc/sysconfig/network-scripts/ifcfg-eth0`

删掉UUID,HWADDR

配置静态地址

`vi /etc/udev/rules.d/70-persistent-net.rules`

删除SUBSYSTEM..

将NAME="eth1"中的eth1改为eth0

----------------------------------------------------------
集群配置记录

Linux01 192.168.200.127
Linux02 192.168.200.126
Linux03 192.168.200.125
Linux04 192.168.200.124
Linux05 192.168.200.123
Linux06 192.168.200.122

./redis-trib.rb create --replicas 1 192.168.200.127:6379 192.168.200.126:6379 192.168.200.125:6379 192.168.200.124:6379 192.168.200.123:6379 192.168.200.122:6379

cd /home/apps/redisinstall/bin

./redis-cli --cluster create 192.168.200.127:6379 192.168.200.126:6379 192.168.200.125:6379 192.168.200.124:6379 192.168.200.123:6379 192.168.200.122:6379 --cluster-replicas 1
