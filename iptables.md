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