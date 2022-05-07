/* ssh端口映射 */
/* telnet 23端口映射 */
ssh -C -f -N -g -L 8023:192.168.254.201:23 admin@192.168.254.201

/* ssh 22端口映射 */
ssh -C -f -N -g -L 8022:192.168.254.201:22 admin@192.168.254.201

/* 80端口映射 */
ssh -C -f -N -g -L 8080:172.31.18.104:80 admin@172.31.18.104

/* 动态端口转发 */
ssh -f -N -D  localhost:9966 admin@172.31.3.129

说明：
ssh -C -f -N -g -L "local port":"dst host":"dst port" "user"@"ssh-server host"
