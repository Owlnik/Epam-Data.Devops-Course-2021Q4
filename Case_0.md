# Homework_1 Kizhnyaev Nikita
## 0)
  1) On 1 vm add net adapter in virtual box with Internal network
  2) Create 2 vm with addapter internal network.
  3) Install centos & run centos
  4) login in root 
  5) ```usermod -a -G wheel nik 
     su nik
     ip a
     sudo ip a add 10.31.110.2/24 dev enp0s3
  6) On 1 vm login in root 
  7) ```usermod -a -G wheel nik 
     su nik
     ip a
     sudo vi /etc/sysconfig/network-scripts/ifcfg-enp0s8
  8) ```ONBOOT="yes"
        DEVICE="enp0s8"
        BOOTPROTO="static"
        IPADDR="10.31.110.3"
        PREFIX="24"```
  9) ```sudo ifdown enp0s8 && sudo ifup enp0s8```
  10) ```ping 10.31.110.2```
  11) ```ssh nik@10.31.110.2```
## 1) 
  1) ```ls /usr/share/man/man{1..9}/*{.,-,_}config{.,-,_}*``` or ```ls /usr/share/man/man{1..9}/*{.,-,_}config{.,-,_}```
  2) ```ls /usr/share/man/man{1,7}/*system*``` or ```ls /usr/share/man/man{1,7}/*{.,-,_}system{.,-,_}```
## 2)
  1) ```find /usr/share/man -name "*help*"```
  2) ```find /usr/share/man -name "conf*"```
  3) ```find /usr/share/man -type d -name "*x" -exec ls -al {} \;``` This command searches for all directories ending in x and prints their contents to the terminal. ```{}``` this construction add every line found like an argument to the command after exec.```\;``` this construction protect from expansion by the shell/
