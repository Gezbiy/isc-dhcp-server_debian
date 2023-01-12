# Setting DHCP & Static With Debian 10
- Konfigurasi IP Address
- Konfigurasi DNS Server
- Konfigurasi DHCP Server

## Konfigurasi IP Address
 
```nano /etc/network/interfaces/```
- Tambahkan script ip static
```   
 #The primary network interfaces
      auto enp0s8
      iface enp0s8 inet static
            address 192.168.67.xx
            netmask 255.255.255.0
```
- Tambahkan script IP DHCP
```
auto eth1 (sesuaikan dengan pc)
    iface eth1 inet dhcp
```
ctrl + x, lalu save
- Restart Network
``` 
/etc/init.d/networking restart
          atau
systemctl networking restart
```
- Reboot system
```
Systemctl reboot
```
cek ip dengan ketik " ip a "

## Konfigurasi dhcp
- Install dhcp
"sebelum melakukan installasi pastikan sudah menambah dvd binary 2"
``` 
apt-get install isc-dhcp-server
```
- Copy Directory
``` 
cp /etc/dhcp/dhcp.conf /etc/dhcp/dhcp.conf.backup
```
- Konfigurasi DHCP
