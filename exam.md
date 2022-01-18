# Экзаменационное задание 
Задача:Установить, настроить и запустить Hadoop Сore в минимальной конфигурации. Для этого потребуется подготовить 2 виртуальные машины: VM1 - headnode; VM2 - worker. Понимание принципов работы Hadoop и его компонентов для успешной сдачи задания не требуется. Все инструкции и команды для каждого шага задания должны быть сохранены в файле.
1) 1. Установить CentOS на 2 виртуальные машины:
VM1: 2CPU, 2-4G памяти, системный диск на 15-20G и дополнительные 2 диска по 5G
VM2: 2CPU, 2-4G памяти, системный диск на 15-20G и дополнительные 2 диска по 5G
Все дальнейшие действия будут выполняться на обеих машинах, если не сказано иначе
2) При установке CentOS создать дополнительного пользователя exam и настроить для него использование sudo без пароля. Все последующие действия необходимо выполнять от этого пользователя, если не указано иное.
``` # useradd -m -G wheel exam ```
```# passwd exam ```
```# visudo```
``` exam    ALL=(ALL)       NOPASSWD: ALL```
```
  sudo -l
  Matching Defaults entries for exam on CentOS7:
      !visiblepw, always_set_home, match_group_by_gid, always_query_group_plugin, env_reset,
      env_keep="COLORS DISPLAY HOSTNAME HISTSIZE KDEDIR LS_COLORS", env_keep+="MAIL PS1 PS2 QTDIR
      USERNAME LANG LC_ADDRESS LC_CTYPE", env_keep+="LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT
      LC_MESSAGES", env_keep+="LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE", env_keep+="LC_TIME
      LC_ALL LANGUAGE LINGUAS _XKB_CHARSET XAUTHORITY", secure_path=/sbin\:/bin\:/usr/sbin\:/usr/bin

  User exam may run the following commands on CentOS7:
      (ALL) NOPASSWD: ALL
```
3) Установить OpenJDK8 из репозитория CentOS.

``` sudo yum install -y java-1.8.0-openjdk ```
``` java -version
  openjdk version "1.8.0_312"
  OpenJDK Runtime Environment (build 1.8.0_312-b07)
  OpenJDK 64-Bit Server VM (build 25.312-b07, mixed mode)
```
4)Скачать архив с Hadoop версии 3.1.2

``` curl -O https://archive.apache.org/dist/hadoop/common/hadoop-3.1.2/hadoop-3.1.2.tar.gz ```
``` md5sum hadoop-3.1.2.tar.gz
      43 94 af 12 a8 14 24 dc 22 5f e4 f2 dd 02 f2 74  hadoop-3.1.2.tar.gz
```
MD5 = 43 94 AF 12 A8 14 24 DC 22 5F E4 F2 DD 02 F2 74
 контрольные суммы совпадают.

5) Распаковать содержимое архива в /opt/hadoop-3.1.2/

``` sudo mkdir /opt/hadoop-3.1.2 ```
``` sudo tar -C "/opt/hadoop-3.1.2/" -xzvf ./hadoop-3.1.2.tar.gz```

6) Сделать симлинк /usr/local/hadoop/current/ на директорию /opt/hadoop-3.1.2/
``` sudo mkdir /usr/local/hadoop ``` 
``` sudo ln -s /opt/hadoop-3.1.2/ /usr/local/hadoop/current```
7) Создать пользователей hadoop, yarn и hdfs, а также группу hadoop, в которую необходимо добавить всех этих пользователей

```
  sudo groupadd hadoop 
  sudo useradd -m -g hadoop hadoop
  sudo useradd -m -g hadoop yarn
  sudo useradd -m -g hadoop hdfs
```
8) Создать для обоих дополнительных дисков разделы размером в 100% диска.
``` 
  sudo fdisk -l
  Disk /dev/sda: 21.5 GB, 21474836480 bytes, 41943040 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk label type: dos
  Disk identifier: 0x0008664c

     Device Boot      Start         End      Blocks   Id  System
  /dev/sda1   *        2048     1050623      524288   83  Linux
  /dev/sda2         1050624    41943039    20446208   8e  Linux LVM

  Disk /dev/sdb: 10.7 GB, 10737418240 bytes, 20971520 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes


  Disk /dev/sdc: 10.7 GB, 10737418240 bytes, 20971520 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes


  Disk /dev/mapper/centos_centos-root: 20.1 GB, 20073938944 bytes, 39206912 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes


  Disk /dev/mapper/centos_centos-swap: 859 MB, 859832320 bytes, 1679360 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
```
```
  sudo fdisk /dev/sdb (вывод анологичен тому как сделано ниже)
  sudo fdisk /dev/sdc
  Welcome to fdisk (util-linux 2.23.2).

  Changes will remain in memory only, until you decide to write them.
  Be careful before using the write command.

  Device does not contain a recognized partition table
  Building a new DOS disklabel with disk identifier 0x28d0b41e.

  Command (m for help): g
  Building a new GPT disklabel (GUID: F04A68F0-FAA6-4291-A0C6-5E7781006E8C)


  Command (m for help): n
  Partition number (1-128, default 1): 1
  First sector (2048-20971486, default 2048):
  Last sector, +sectors or +size{K,M,G,T,P} (2048-20971486, default 20971486):
  Created partition 1


  Command (m for help): t
  Selected partition 1
  Partition type (type L to list all types): 31
  Changed type of partition 'Linux filesystem' to 'Linux LVM'
```
```
    lsblk
  NAME                   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
  sda                      8:0    0   20G  0 disk
  ├─sda1                   8:1    0  512M  0 part /boot
  └─sda2                   8:2    0 19.5G  0 part
    ├─centos_centos-root 253:0    0 18.7G  0 lvm  /
    └─centos_centos-swap 253:1    0  820M  0 lvm  [SWAP]
  sdb                      8:16   0   10G  0 disk
  └─sdb1                   8:17   0   10G  0 part
  sdc                      8:32   0   10G  0 disk
  └─sdc1                   8:33   0   10G  0 part
  sr0                     11:0    1 1024M  0 rom
```
9) Инициализировать разделы из п.8 в качестве физических томов для LVM.
