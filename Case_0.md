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
## 3) 
  1) ```tail -n -2 /etc/yum.conf```
  2) ```head --lines 7 /etc/fstab```
  3) ``` head -n 30 /etc/fstab | wc -l```
   
     ```11``` this command print all file
## 4)
  1) ```touch file_name{1..3}.md```
  2) ```mv ./file_name1.{md,textdoc}```
  3) ```mv ./file_name2{.md,}```
  4) ```mv ./file_name3.md{,.latest}```
  5) ```mv ./file_name1.{textdoc,txt}```
## 5)
  1) ```cd```
  2) ```cd ~ ```
  3) ```cd - ```
  4) ```cd $HOME```
  5) ```cd /home/$USER```
  6) ```cd ../home/$USER```
  7) and many more options
## 6)
  1) ```mkdir -p ./{new,in-process/tread{0..2},processed}```
  2) ```touch ./new/data{0..9}{0..9}```
  3) ```cp ./new/data{00..33} ./in-process/tread0```
  4) ```cp ./new/data{34..66} ./in-process/tread1```
  5) ```cp ./new/data{67..99} ./in-process/tread2```
  6) ```ls -R ./in-process/```
  7) ```mv ./in-process/*/* ./processed/```
  8) ```ls -R ./processed/ ./in-process/```
  9) ``` if [ $(ls ./new | wc -l) == $(ls ./processed/ | wc -l) ]; then rm ./new/*; fi```
## 7)
  1)```a=1```
  2)```b=3```
  3) ```eval echo file{$a..$b}```
