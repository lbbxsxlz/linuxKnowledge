## how to build iptables
./configure --host=arm-linux --target=arm-linux CC=arm-linux-gcc --prefix=/home/tools/iptables/iptables-1.8.4_dv300 --enable-static --disable-shared --disable-nftables --with-xt-lock-name=/tmp/xtables.lock

增加--static的参数。
Makefile
utils/Makefile
include/Makefile
libxtables/Makefile
libiptc/Makefile
iptables/Makefile
libipq/Makefile

sed -i 's/CFLAGS = -g -O2/CFLAGS = -g -O2 --static/' Makefile
make clean;make

## port forward
/*iptables 端口转发 访问172.31.18.104:80 */
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A PREROUTING (-d 172.31.58.213) -p tcp --dport 8080 -j DNAT --to-destination 172.31.18.104:80
iptables -t nat -A POSTROUTING -d 172.31.18.104 -p tcp --dport 80 -j SNAT --to 172.31.58.213 或
iptables -t nat -A POSTROUTING -j MASQUERADE

iptables -nL -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       tcp  --  0.0.0.0/0            172.31.58.213        tcp dpt:8080 to:172.31.18.104:80

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
SNAT       tcp  --  0.0.0.0/0            172.31.18.104        tcp dpt:80 to:172.31.58.213

带VLAN的设备配置  172.31.11.108 与 192.168.254.254 同网卡
iptables -t nat -A PREROUTING (-d 172.31.11.108) -p tcp --dport 8022 -j DNAT --to-destination 192.168.254.201:22
iptables -t nat -A POSTROUTING -d 192.168.254.201 -p tcp --dport 22 -j SNAT --to 192.168.254.254  或
iptables -t nat -A POSTROUTING -j MASQUERADE

说明：
iptables -t nat -A PREROUTING  (-i "ethdev" -d "对外公网ip") -p tcp --dport "对外端口" -j DNAT --to "内部实际提供服务的ip":"实际提供服务的端口"
iptables -t nat -A POSTROUTING -o "ethdev" -d "内部实际提供服务的ip" -p tcp --dport "实际提供服务的端口" -j SNAT --to-source "运行iptables机器的内网ip"

/* iptables NAT */
echo 1 > /proc/sys/net/ipv4/ip_forward
//iptables -A FORWARD -i eth0 -o lte0 -j ACCEPT
//iptables -A FORWARD -i eth0 -o lte0 -m state --state ESTABLISHED,RELATED  -j ACCEPT
iptables -t nat -A POSTROUTING -o lte0 -j MASQUERADE

/* iptables NAT Ubuntu Success IP 访问 */
Ubuntu 添加默认路由
sudo route add default gw 172.31.1.100  (sudo route del default)
设置dns服务器 /etc/resolv.conf 添加nameserver 223.5.5.5

设备端（有线IP 172.31.1.100， 10.61.148.170 4G的虚拟IP）设置转发
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 172.31.0.0/16 -j SNAT --to 10.61.148.170

iptables -t nat -A PREROUTING -p tcp --dport 8022 -j DNAT --to-destination 192.168.1.65:22
iptables -t nat -A PREROUTING -p tcp --dport 9022 -j DNAT --to-destination 192.168.1.100:22

/* 22端口映射 */
iptables -t nat -A PREROUTING -p tcp --dport 8022 -j DNAT --to-destination 192.168.1.7:22
iptables -t nat -A POSTROUTING -d 192.168.1.7 -p tcp --dport 22 -j SNAT --to 192.168.1.1

/* 80 端口映射 */
iptables -t nat -A PREROUTING -p tcp --dport 8880 -j DNAT --to-destination 192.168.1.7:80
iptables -t nat -A POSTROUTING -d 192.168.1.7 -p tcp --dport 80 -j SNAT --to 192.168.1.1

/* NAT全映射 */
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -t nat -A PREROUTING -j DNAT --to-destination 192.168.1.7