#0)
 ##START 
  1) On 1 vm add net adapter in virtual box with Internal network
  2) Create 2 vm with addapter internal network.
  3) Install centos & run centos
  4) login in root 
  5) ```usermod -a -G wheel nik 
     su nik
     ip a
     sudo ip a add 10.31.110.2/24 dev enp0s3```
  6) On 1 vm login in root 
  7) ```usermod -a -G wheel nik 
     su nik
     ip a
     sudo vi /etc/sysconfig/network-scripts/ifcfg-enp0s8```
  8)```ONBOOT="yes"
    DEVICE="enp0s8"
    BOOTPROTO="static"
    IPADDR="10.31.110.3"
    PREFIX="24"```
  9)```ping 10.31.110.2```
  10)```ssh nik@10.31.110.2```
 ##DONE
