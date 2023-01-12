# Setting DHCP & Static With Debian 10
- Konfigurasi IP Address
- Konfigurasi DNS Server
- Konfigurasi DHCP Server

## Konfigurasi IP Address
 
```nano /etc/network/interfaces/```
- Tambahkan script ip static
```   
auto eth1
      iface eth1 inet static
            address 192.168.67.xx
            netmask 255.255.255.0
            gateway 192.168.67.1
```
