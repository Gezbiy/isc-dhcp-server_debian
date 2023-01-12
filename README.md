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
