/* tftp从服务器拷贝文件 */
tftp -g -r ethtool 10.34.11.249

/* tftp拷贝文件到服务器 */
tftp -p -r ethtool 10.34.11.249

/* tftpd 服务开启 */
udpsvd -vE 0.0.0.0 69 tftpd /mnt/mtd/Config &

/* tftp-hpa编译与运行 */
 ./configure --host=arm-himix200-linux --target=arm-himix200-linux CC=arm-himix200-linux-gcc --prefix=/home/31770/tools/tftp-hpa/arm-himix200-linux
in.tftpd -l -c -u root -s /mnt/mtd/
tftp 10.34.11.45 -c get Clover.rar
