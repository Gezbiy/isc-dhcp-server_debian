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
            address 192.168.xx.19
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
```
atau
```
systemctl networking restart
```
- Reboot system
```
Systemctl reboot
```
cek ip dengan ketik " ip a "

## Konfigurasi dhcp
- Install dhcp
``` 
apt-get install isc-dhcp-server
```
"sebelum melakukan installasi pastikan sudah menambah dvd binary 2"
- Copy Directory
``` 
cp /etc/dhcp/dhcp.conf /etc/dhcp/dhcp.conf.backup
```
- Konfigurasi DHCP
```
nano /etc/dhcp/dhcp.conf/
```
scroll dan cari
```
 # A slightly different configuration for an internal subnet.
   subnet 192.168.xx.0 netmask 255.255.255.0{
   range 192.168.xx.5 192.168.xx.57; 
   option domain-name-server 192.168.xx.19; (masukan ip yang sama saat setting ip address)
   option domain-name "namakamu.com"; 
   option routers 192.168.xx.1;
   option broadcast-address 192.168.xx.31;
   default-lease-time 600;
   max-lease-time 7200;
   }
```
"input ip yang sama saat melakukan setting ip diawal" (ctrl + x, lalu save)
- setting interface dhcp
```
nano /etc/default/isc-dhcp-server
```
pada bagian ( interfacev4=" " ), sesuaikan dengan keadaan pc masing masing contoh;
```
INTERFACEv4="enp0s8"
```
- Restart dhcp
```
/etc/init.d/isc-dhcp-server
```
atau
```
systemctl restart isc-dhcp-server
```
- cek status dhcp
```
/etc/init.d/isc-dhcp-server status
```
atau
```
systemctl status isc-dhcp-server
```
jika status sudah running maka tanda nya anda sudah berhasil
- periksa ip bagian "enp0s8"
```
ip a
```
jika sudahh muncul ip yang sudah di setting sebelumnya, maka sudah selesai
