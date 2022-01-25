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

``` sudo pvcreate /dev/sdb1
    Physical volume "/dev/sdb1" successfully created.
    sudo pvcreate /dev/sdc1
    Physical volume "/dev/sdc1" successfully created.
    sudo pvscan
    PV /dev/sda2   VG centos_centos   lvm2 [<19.50 GiB / 0    free]
    PV /dev/sdc1                      lvm2 [<10.00 GiB]
    PV /dev/sdb1                      lvm2 [<10.00 GiB]
    Total: 3 [39.49 GiB] / in use: 1 [<19.50 GiB] / in no VG: 2 [<20.00 GiB]
```
10) Создать две группы LVM и добавить в каждую из них по одному физическому тому из п.9
``` 
  sudo vgcreate vg1 /dev/sdb1
  Volume group "vg1" successfully created
  sudo vgcreate vg2 /dev/sdc1
  Volume group "vg2" successfully created
  sudo vgscan
  Reading volume groups from cache.
  Found volume group "centos_centos" using metadata type lvm2
  Found volume group "vg1" using metadata type lvm2
  Found volume group "vg2" using metadata type lvm2
```
11) В каждой из групп из п.10 создать логический том LVM размером 100% группы.

```
    sudo lvcreate -l +100%FREE -n lv2 vg2
    Logical volume "lv2" created.
    sudo lvcreate -l +100%FREE -n lv1 vg1
    Logical volume "lv1" created.
    sudo lvscan
    ACTIVE            '/dev/centos_centos/root' [<18.70 GiB] inherit
    ACTIVE            '/dev/centos_centos/swap' [820.00 MiB] inherit
    ACTIVE            '/dev/vg1/lv1' [<10.00 GiB] inherit
    ACTIVE            '/dev/vg2/lv2' [<10.00 GiB] inherit
```
12) На каждом логическом томе LVM создать файловую систему ext4.

```
  sudo mkfs.ext4 /dev/vg1/lv1
  mke2fs 1.42.9 (28-Dec-2013)
  Filesystem label=
  OS type: Linux
  Block size=4096 (log=2)
  Fragment size=4096 (log=2)
  Stride=0 blocks, Stripe width=0 blocks
  655360 inodes, 2620416 blocks
  131020 blocks (5.00%) reserved for the super user
  First data block=0
  Maximum filesystem blocks=2151677952
  80 block groups
  32768 blocks per group, 32768 fragments per group
  8192 inodes per group
  Superblock backups stored on blocks:
          32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

  Allocating group tables: done
  Writing inode tables: done
  Creating journal (32768 blocks): done
  Writing superblocks and filesystem accounting information: done 

  sudo mkfs.ext4 /dev/vg2/lv2
  mke2fs 1.42.9 (28-Dec-2013)
  Filesystem label=
  OS type: Linux
  Block size=4096 (log=2)
  Fragment size=4096 (log=2)
  Stride=0 blocks, Stripe width=0 blocks
  655360 inodes, 2620416 blocks
  131020 blocks (5.00%) reserved for the super user
  First data block=0
  Maximum filesystem blocks=2151677952
  80 block groups
  32768 blocks per group, 32768 fragments per group
  8192 inodes per group
  Superblock backups stored on blocks:
          32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

  Allocating group tables: done
  Writing inode tables: done
  Creating journal (32768 blocks): done
  Writing superblocks and filesystem accounting information: done 

    lsblk -f
    NAME                   FSTYPE      LABEL UUID                                   MOUNTPOINT
    sda
    ├─sda1                 xfs               dd3da66e-5ba8-4b24-b23d-2caceabd0508   /boot
    └─sda2                 LVM2_member       2o4p2P-rNMJ-dPuv-soss-xi3i-3yfz-674qaY
      ├─centos_centos-root xfs               00c2b98e-1247-45fe-8931-d06f57d788b4   /
      └─centos_centos-swap swap              7a28f385-24f1-4563-90ee-88c5e7de47bf   [SWAP]
    sdb
    └─sdb1                 LVM2_member       avVU74-dWPe-wiho-1nm7-YWrj-ckVx-ps0ifT
      └─vg1-lv1            ext4              9b134ae8-a09e-4656-9232-862b548dd254
    sdc
    └─sdc1                 LVM2_member       d62Laj-Yxqa-sBYX-fJuH-5c8y-NFlp-T2DY3L
      └─vg2-lv2            ext4              de9e4827-9df8-4ed7-a00e-aa2c686f818d
    sr0
```
13) Создать директории и использовать их в качестве точек монтирования файловых систем из п.12:

```
  sudo mkdir /opt/mount1
  sudo mkdir /opt/mount2
  ls -al /opt
  total 0
  drwxr-xr-x.  5 root root  54 Jan 20 08:56 .
  dr-xr-xr-x. 17 root root 284 Jan 13 10:50 ..
  drwxr-xr-x.  3 root root  26 Jan 18 10:15 hadoop-3.1.2
  drwxr-xr-x.  2 root root   6 Jan 20 08:55 mount1
  drwxr-xr-x.  2 root root   6 Jan 20 08:56 mount2
```
14) Настроить систему так, чтобы монтирование происходило автоматически при запуске системы. Произвести монтирование новых файловых систем.

```
  sudo mount /dev/vg1/lv1 /opt/mount1/
  sudo mount /dev/vg2/lv2 /opt/mount2/
  df -hT
  Filesystem                     Type      Size  Used Avail Use% Mounted on
  devtmpfs                       devtmpfs  1.9G     0  1.9G   0% /dev
  tmpfs                          tmpfs     1.9G     0  1.9G   0% /dev/shm
  tmpfs                          tmpfs     1.9G   35M  1.9G   2% /run
  tmpfs                          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
  /dev/mapper/centos_centos-root xfs        19G  3.2G   16G  17% /
  /dev/sda1                      xfs       509M  218M  291M  43% /boot
  tmpfs                          tmpfs     379M     0  379M   0% /run/user/1000
  /dev/mapper/vg1-lv1            ext4      9.8G   37M  9.2G   1% /opt/mount1
  /dev/mapper/vg2-lv2            ext4      9.8G   37M  9.2G   1% /opt/mount2 

  sudo vim /etc/fstab
    #
    # /etc/fstab
    # Created by anaconda on Sat May 30 17:20:38 2020
    #
    # Accessible filesystems, by reference, are maintained under '/dev/disk'
    # See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
    #
    /dev/mapper/centos_centos-root /                       xfs     defaults        0 0
    UUID=dd3da66e-5ba8-4b24-b23d-2caceabd0508 /boot                   xfs     defaults        0 0
    /dev/mapper/centos_centos-swap swap                    swap    defaults        0 0
    /dev/vg1/lv1 /opt/mount1        ext4    defaults        0 0
    /dev/vg2/lv2 /opt/mount2        ext4    defaults        0 0
```
15) После монтирования создать 2 директории для хранения файлов Namenode сервиса HDFS:

``` sudo mkdir /opt/mount{1..2}/namenode-dir ```

16. Сделать пользователя hdfs и группу hadoop владельцами этих директорий.

``` sudo chown hdfs:hadoop /opt/mount{1..2}/namenode-dir```
```
  ls -al /opt/mount{1..2}
  /opt/mount1:
  total 24
  drwxr-xr-x. 4 root root    4096 Jan 20 09:30 .
  drwxr-xr-x. 5 root root      54 Jan 20 08:56 ..
  drwx------. 2 root root   16384 Jan 20 08:50 lost+found
  drwxr-xr-x. 2 hdfs hadoop  4096 Jan 20 09:30 namenode-dir

  /opt/mount2:
  total 24
  drwxr-xr-x. 4 root root    4096 Jan 20 09:30 .
  drwxr-xr-x. 5 root root      54 Jan 20 08:56 ..
  drwx------. 2 root root   16384 Jan 20 08:51 lost+found
  drwxr-xr-x. 2 hdfs hadoop  4096 Jan 20 09:30 namenode-dir
```
17) После монтирования создать 2 директории для хранения файлов Datanode сервиса HDFS:
```
  sudo mkdir /opt/mount{1..2}/datanode-dir
  ls -al /opt/mount{1..2}
  /opt/mount1:
  total 24
  drwxr-xr-x. 4 root root  4096 Jan 24 06:02 .
  drwxr-xr-x. 5 root root    54 Jan 22 14:06 ..
  drwxr-xr-x. 2 root root  4096 Jan 24 06:02 datanode-dir
  drwx------. 2 root root 16384 Jan 22 14:05 lost+found

  /opt/mount2:
  total 24
  drwxr-xr-x. 4 root root  4096 Jan 24 06:02 .
  drwxr-xr-x. 5 root root    54 Jan 22 14:06 ..
  drwxr-xr-x. 2 root root  4096 Jan 24 06:02 datanode-dir
  drwx------. 2 root root 16384 Jan 22 14:05 lost+found  
```
18) Сделать пользователя hdfs и группу hadoop владельцами директорий из п.17.

```
  sudo chown hdfs:hadoop /opt/mount{1..2}/datanode-dir
  ls -al /opt/mount{1..2}
  /opt/mount1:
  total 24
  drwxr-xr-x. 4 root root    4096 Jan 24 06:02 .
  drwxr-xr-x. 5 root root      54 Jan 22 14:06 ..
  drwxr-xr-x. 2 hdfs hadoop  4096 Jan 24 06:02 datanode-dir
  drwx------. 2 root root   16384 Jan 22 14:05 lost+found

  /opt/mount2:
  total 24
  drwxr-xr-x. 4 root root    4096 Jan 24 06:02 .
  drwxr-xr-x. 5 root root      54 Jan 22 14:06 ..
  drwxr-xr-x. 2 hdfs hadoop  4096 Jan 24 06:02 datanode-dir
  drwx------. 2 root root   16384 Jan 22 14:05 lost+found  
```
19) Создать дополнительные 4 директории для Nodemanager сервиса YARN

```
  sudo mkdir /opt/mount{1..2}/nodemanager-local-dir
  sudo mkdir /opt/mount{1..2}/nodemanager-log-dir
  ls -al /opt/mount{1..2}
  /opt/mount1:
  total 32
  drwxr-xr-x. 6 root root    4096 Jan 24 06:24 .
  drwxr-xr-x. 5 root root      54 Jan 22 14:06 ..
  drwxr-xr-x. 2 hdfs hadoop  4096 Jan 24 06:02 datanode-dir
  drwx------. 2 root root   16384 Jan 22 14:05 lost+found
  drwxr-xr-x. 2 root root    4096 Jan 24 06:24 nodemanager-local-dir
  drwxr-xr-x. 2 root root    4096 Jan 24 06:24 nodemanager-log-dir

  /opt/mount2:
  total 32
  drwxr-xr-x. 6 root root    4096 Jan 24 06:24 .
  drwxr-xr-x. 5 root root      54 Jan 22 14:06 ..
  drwxr-xr-x. 2 hdfs hadoop  4096 Jan 24 06:02 datanode-dir
  drwx------. 2 root root   16384 Jan 22 14:05 lost+found
  drwxr-xr-x. 2 root root    4096 Jan 24 06:24 nodemanager-local-dir
  drwxr-xr-x. 2 root root    4096 Jan 24 06:24 nodemanager-log-dir
```
20) Сделать пользователя yarn и группу hadoop владельцами директорий из п.19.

```
  sudo chown yarn:hadoop /opt/mount{1..2}/nodemanager-local-dir
  [exam@CentOS7 ~]$ sudo chown yarn:hadoop /opt/mount{1..2}/nodemanager-log-dir
  [exam@CentOS7 ~]$ ls -al /opt/mount{1..2}
  /opt/mount1:
  total 32
  drwxr-xr-x. 6 root root    4096 Jan 24 06:24 .
  drwxr-xr-x. 5 root root      54 Jan 22 14:06 ..
  drwxr-xr-x. 2 hdfs hadoop  4096 Jan 24 06:02 datanode-dir
  drwx------. 2 root root   16384 Jan 22 14:05 lost+found
  drwxr-xr-x. 2 yarn hadoop  4096 Jan 24 06:24 nodemanager-local-dir
  drwxr-xr-x. 2 yarn hadoop  4096 Jan 24 06:24 nodemanager-log-dir

  /opt/mount2:
  total 32
  drwxr-xr-x. 6 root root    4096 Jan 24 06:24 .
  drwxr-xr-x. 5 root root      54 Jan 22 14:06 ..
  drwxr-xr-x. 2 hdfs hadoop  4096 Jan 24 06:02 datanode-dir
  drwx------. 2 root root   16384 Jan 22 14:05 lost+found
  drwxr-xr-x. 2 yarn hadoop  4096 Jan 24 06:24 nodemanager-local-dir
  drwxr-xr-x. 2 yarn hadoop  4096 Jan 24 06:24 nodemanager-log-dir 
```
21) Настроить доступ по SSH, используя ключи для пользователя hadoop.
```
  sudo ssh-keygen -t ed25519 -f /home/hadoop/.ssh/key2
  sudo chmod 600 /home/hadoop/.ssh/key2
  sudo chmod 600 /home/hadoop/.ssh/key2.pub
  sudo chown -R hadoop:hadoop /home/hadoop/.ssh
  sudo vim /home/hadoop/.ssh/config
   Host workernode
    HostName 78.140.242.55
    PreferredAuthentications publickey
    IdentityFile /home/hadoop/.ssh/key1
    User hadoop
  sudo ssh-copy-id -i /home/hadoop/.ssh/key2.pub hadoop@78.140.242.57
```
При тестовом подключении возникла ошибка 
workernode/home/hadoop/.ssh/config: line 7: Bad configuration option: ~
решение проблемы было найдено после вывода конфига на консоль и коследующего удаления тильды в последней строке.

```
22) Добавить VM1 и VM2 в /etc/hosts.
```
  sudo vim /etc/hosts
      127.0.0.1   localhost localhost.localdomain localhost4 localhost4.locald127.0.0.1   localhost localhost.localdomain localhost4 localhost4.locald127.0.0.1   localhost localhost.localdomain localhost4 localhost4.locald127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
    ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

    ::1 vm2

    78.140.242.57   vm1

    78.140.242.55   vm2
```
23) Скачать файлы по ссылкам в /usr/local/hadoop/current/etc/hadoop/{hadoop-env.sh,core-site.xml,hdfs-site.xml,yarn-site.xml}. При помощи sed заменить заглушки на необходимые значения

```
  sudo mkdir -p /usr/local/hadoop/current/etc/hadoop/
  cd /usr/local/hadoop/current/etc/hadoop/
  sudo yum install git
  sudo git clone https://gist.github.com/64b9abd1700e15f04147ea48bc72b3c7.git
  sudo git clone https://gist.github.com/2bedf24fd2721bad276e416b57d63e38.git
  sudo git clone https://gist.github.com/ba87c0072cd51aa85c9ee6334cc99158.git
  sudo git clone https://gist.github.com/2f42f248f02aeda18105805493bb0e9b.git
  sudo mv 2bedf24fd2721bad276e416b57d63e38/hdfs-site.xml ./hdfs-site.xml
  sudo mv 64b9abd1700e15f04147ea48bc72b3c7/core-site.xml ./core-site.xml
  sudo mv ba87c0072cd51aa85c9ee6334cc99158/yarn-site.xml ./yarn-site.xml
  sudo mv 2f42f248f02aeda18105805493bb0e9b/hadoop-env.sh ./hadoop-env.sh
  sudo sed -i 's/\"\%PATH_TO_OPENJDK8_INSTALLATION\%\"/\/usr\/share\/java-1.8.0/' ./hadoop-env.sh
  sudo grep JAVA_HOME ./hadoop-env.sh
    \#  JAVA_HOME=/usr/java/testing hdfs dfs -ls
    \# Technically, the only required environment variable is JAVA_HOME.
     export JAVA_HOME=/usr/share/java-1.8.0
  sudo sed -i 's/\"\%PATH_TO_HADOOP_INSTALLATION\"/\/usr\/local\/hadoop\/current/' ./hadoop-env.sh
  grep HADOOP_HOME hadoop-env.sh
    export HADOOP_HOME=/usr/local/hadoop/current
    \# export HADOOP_CONF_DIR=${HADOOP_HOME}/etc/hadoop
    \# ${HADOOP_HOME}/logs by default.
    \# export HADOOP_LOG_DIR=${HADOOP_HOME}/logs
  sudo sed -i 's/\"\%HADOOP_HEAP_SIZE\%\"/512/' ./hadoop-env.sh
  grep HADOOP_HEAPSIZE_MAX ./hadoop-env.sh
    export HADOOP_HEAPSIZE_MAX=512
  sudo sed -i 's/\%HDFS_NAMENODE_HOSTNAME\%/vm1/' ./core-site.xml 
  grep vm1 ./core-site.xml
    <value>hdfs://vm1:8020</value>
  sudo sed -i 's/\%NAMENODE_DIRS\%/\/opt\/mount1\/namenode-dir,\/opt\/mount2\/namenode-dir/' ./hdfs-site.xml
  grep mount ./hdfs-site.xml
      <value>/opt/mount1/namenode-dir,/opt/mount2/namenode-dir</value>
  sudo sed -i 's/\%DATANODE_DIRS\%/\/opt\/mount1\/datanode-dir,\/opt\/mount2\/datanode-dir/' ./hdfs-site.xml
  grep mount ./hdfs-site.xml
      <value>/opt/mount1/namenode-dir,/opt/mount2/namenode-dir</value>
      <value>/opt/mount1/datanode-dir,/opt/mount2/datanode-dir</value>
  sudo sed -i 's/\%YARN_RESOURCE_MANAGER_HOSTNAME\%/vm1/' ./yarn-site.xml
  grep vm1 ./yarn-site.xml
      <value>vm1</value>
  sudo sed -i 's/\%NODE_MANAGER_LOCAL_DIR\%/\/opt\/mount1\/nodemanager-local-dir,\/opt\/mount2\/nodemanager-local-dir/' ./yarn-site.xml
    grep mount ./yarn-site.xml
      <value>/opt/mount1/nodemanager-local-dir,/opt/mount2/nodemanager-local-dir</value>
  sudo sed -i 's/\%NODE_MANAGER_LOG_DIR\%/\/opt\/mount1\/nodemanager-log-dir,\/opt\/mount2\/nodemanager-log-dir/' ./yarn-site.xml
  grep mount ./yarn-site.xml
      <value>/opt/mount1/nodemanager-local-dir,/opt/mount2/nodemanager-local-dir</value>
      <value>/opt/mount1/nodemanager-log-dir,/opt/mount2/nodemanager-log-dir</value>

  sudo scp -r ./etc root@78.140.242.55:/usr/local/hadoop/current
```
24) Задать переменную окружения HADOOP_HOME через /etc/profile

```
  sudo vim /etc/profile
  HADOOP_HOME=/usr/local/hadoop/current
  source /etc/profile
  echo $HADOOP_HOME
    /usr/local/hadoop/current
```
25)
