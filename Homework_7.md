
## 1 Repositories and Packages
1) Download sysstat package.
  ```
   sudo yum install  --downloadonly --downloaddir=/home/nik/homework sysstat
  Last metadata expiration check: 2:56:55 ago on Sat 25 Dec 2021 03:57:13 PM GMT.
  Dependencies resolved.
  ===================================================================================================================================================================================
   Package                                 Architecture                   Version                                                    Repository                                 Size
  ===================================================================================================================================================================================
  Installing:
   sysstat                                 x86_64                         11.7.3-6.0.1.el8                                           ol8_appstream                             425 k
  Installing dependencies:
   lm_sensors-libs                         x86_64                         3.4.0-23.20180522git70f7e08.el8                            ol8_baseos_latest                          59 k

  Transaction Summary
  ===================================================================================================================================================================================
  Install  2 Packages

  Total download size: 484 k
  Installed size: 1.5 M
  YUM will only download packages for the transaction.
  Is this ok [y/N]:y 
  Downloading Packages:
  (1/2): lm_sensors-libs-3.4.0-23.20180522git70f7e08.el8.x86_64.rpm                                                                                  509 kB/s |  59 kB     00:00    
  (2/2): sysstat-11.7.3-6.0.1.el8.x86_64.rpm                                                                                                         2.6 MB/s | 425 kB     00:00    
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Total                                                                                                                                              2.9 MB/s | 484 kB     00:00     
  Complete!
  The downloaded packages were saved in cache until the next successful transaction.
  You can remove cached packages by executing 'yum clean packages'.
```
2) Get information from downloaded sysstat package file.
```
  rpm -qi sysstat-11.7.3-6.0.1.el8.x86_64.rpm  
  Name        : sysstat
  Version     : 11.7.3
  Release     : 6.0.1.el8
  Architecture: x86_64
  Install Date: (not installed)
  Group       : Applications/System
  Size        : 1473963
  License     : GPLv2+
  Signature   : RSA/SHA256, Wed 10 Nov 2021 02:53:58 PM GMT, Key ID 82562ea9ad986da3
  Source RPM  : sysstat-11.7.3-6.0.1.el8.src.rpm
  Build Date  : Wed 10 Nov 2021 02:51:55 PM GMT
  Build Host  : build-ol8-x86_64.oracle.com
  Relocations : (not relocatable)
  Vendor      : Oracle America
  URL         : http://sebastien.godard.pagesperso-orange.fr/
  Summary     : Collection of performance monitoring tools for Linux
  Description :
  The sysstat package contains the sar, sadf, mpstat, iostat, tapestat,
  pidstat, cifsiostat and sa tools for Linux.
  The sar command collects and reports system activity information.
  The information collected by sar can be saved in a file in a binary
  format for future inspection. The statistics reported by sar concern
  I/O transfer rates, paging activity, process-related activities,
  interrupts, network activity, memory and swap space utilization, CPU
  utilization, kernel activities and TTY statistics, among others. Both
  UP and SMP machines are fully supported.
  The sadf command may  be used to display data collected by sar in
  various formats (CSV, XML, etc.).
  The iostat command reports CPU utilization and I/O statistics for disks.
  The tapestat command reports statistics for tapes connected to the system.
  The mpstat command reports global and per-processor statistics.
  The pidstat command reports statistics for Linux tasks (processes).
  The cifsiostat command reports I/O statistics for CIFS file systems.
```
3) Install sysstat package and get information about files installed by this package.

```sudo rpm -i lm_sensors-libs-3.4.0-23.20180522git70f7e08.el8.x86_64.rpm sysstat-11.7.3-6.0.1.el8.x86_64.rpm```
```
  sudo rpm -ql sysstat
  /etc/profile.d/colorsysstat.csh
  /etc/profile.d/colorsysstat.sh
  /etc/sysconfig/sysstat
  /etc/sysconfig/sysstat.ioconf
  /usr/bin/cifsiostat
  /usr/bin/iostat
  /usr/bin/mpstat
  /usr/bin/pidstat
  /usr/bin/sadf
  /usr/bin/sar
  /usr/bin/tapestat
  /usr/lib/.build-id
  /usr/lib/.build-id/3d
  /usr/lib/.build-id/3d/cc738e133818c61b8da3ff85f2dbc4803f7f4f
  /usr/lib/.build-id/55
  /usr/lib/.build-id/55/2b979d982dad53144ce646c7292b60b52b070c
  /usr/lib/.build-id/58
  /usr/lib/.build-id/58/be8aa2cce65c7d1b84a2af150c0e83fd8b244b
  /usr/lib/.build-id/58/e18511b69b3aa87e92f7223266a7ddd20f2827
  /usr/lib/.build-id/bd
  /usr/lib/.build-id/bd/7627490a7a37fbfbaf9c4a6ba5a4e88e94cc8a
  /usr/lib/.build-id/c2
  /usr/lib/.build-id/c2/cb8c4f4414890c8128d2609fc181df87302a6d
  /usr/lib/.build-id/db
  /usr/lib/.build-id/db/ec9dd82748cab85597cb64ea95463a1c69b6a2
  /usr/lib/.build-id/ff
  /usr/lib/.build-id/ff/3f9d0be5bb9c8ec9e2045712b15507f53b34d1
  /usr/lib/systemd/system/sysstat-collect.service
  /usr/lib/systemd/system/sysstat-collect.timer
  /usr/lib/systemd/system/sysstat-summary.service
  /usr/lib/systemd/system/sysstat-summary.timer
  /usr/lib/systemd/system/sysstat.service
  /usr/lib64/sa
  /usr/lib64/sa/sa1
  /usr/lib64/sa/sa2
  /usr/lib64/sa/sadc
  /usr/share/doc/sysstat
  /usr/share/doc/sysstat/CHANGES
  /usr/share/doc/sysstat/COPYING
  /usr/share/doc/sysstat/CREDITS
  /usr/share/doc/sysstat/FAQ.md
  /usr/share/doc/sysstat/README.md
  /usr/share/doc/sysstat/sysstat-11.7.3.lsm
  /usr/share/locale/af/LC_MESSAGES/sysstat.mo
  /usr/share/locale/cs/LC_MESSAGES/sysstat.mo
  /usr/share/locale/da/LC_MESSAGES/sysstat.mo
  /usr/share/locale/de/LC_MESSAGES/sysstat.mo
  /usr/share/locale/eo/LC_MESSAGES/sysstat.mo
  /usr/share/locale/es/LC_MESSAGES/sysstat.mo
  /usr/share/locale/eu/LC_MESSAGES/sysstat.mo
  /usr/share/locale/fi/LC_MESSAGES/sysstat.mo
  /usr/share/locale/fr/LC_MESSAGES/sysstat.mo
  /usr/share/locale/fur/LC_MESSAGES/sysstat.mo
  /usr/share/locale/gl/LC_MESSAGES/sysstat.mo
  /usr/share/locale/hr/LC_MESSAGES/sysstat.mo
  /usr/share/locale/hu/LC_MESSAGES/sysstat.mo
  /usr/share/locale/id/LC_MESSAGES/sysstat.mo
  /usr/share/locale/it/LC_MESSAGES/sysstat.mo
  /usr/share/locale/ja/LC_MESSAGES/sysstat.mo
  /usr/share/locale/ko/LC_MESSAGES/sysstat.mo
  /usr/share/locale/ky/LC_MESSAGES/sysstat.mo
  /usr/share/locale/lv/LC_MESSAGES/sysstat.mo
  /usr/share/locale/mt/LC_MESSAGES/sysstat.mo
  /usr/share/locale/nb/LC_MESSAGES/sysstat.mo
  /usr/share/locale/nl/LC_MESSAGES/sysstat.mo
  /usr/share/locale/nn/LC_MESSAGES/sysstat.mo
  /usr/share/locale/pl/LC_MESSAGES/sysstat.mo
  /usr/share/locale/pt/LC_MESSAGES/sysstat.mo
  /usr/share/locale/pt_BR/LC_MESSAGES/sysstat.mo
  /usr/share/locale/ro/LC_MESSAGES/sysstat.mo
  /usr/share/locale/ru/LC_MESSAGES/sysstat.mo
  /usr/share/locale/sk/LC_MESSAGES/sysstat.mo
  /usr/share/locale/sr/LC_MESSAGES/sysstat.mo
  /usr/share/locale/sv/LC_MESSAGES/sysstat.mo
  /usr/share/locale/tr/LC_MESSAGES/sysstat.mo
  /usr/share/locale/uk/LC_MESSAGES/sysstat.mo
  /usr/share/locale/vi/LC_MESSAGES/sysstat.mo
  /usr/share/locale/zh_CN/LC_MESSAGES/sysstat.mo
  /usr/share/locale/zh_TW/LC_MESSAGES/sysstat.mo
  /usr/share/man/man1/cifsiostat.1.gz
  /usr/share/man/man1/iostat.1.gz
  /usr/share/man/man1/mpstat.1.gz
  /usr/share/man/man1/pidstat.1.gz
  /usr/share/man/man1/sadf.1.gz
  /usr/share/man/man1/sar.1.gz
  /usr/share/man/man1/tapestat.1.gz
  /usr/share/man/man5/sysstat.5.gz
  /usr/share/man/man8/sa1.8.gz
  /usr/share/man/man8/sa2.8.gz
  /usr/share/man/man8/sadc.8.gz
  /var/log/sa
```
## 2

1) Check if NGINX repository enabled or not.
```

    sudo yum install yum-utils
    [sudo] password for nik: 
    Last metadata expiration check: 3:13:19 ago on Sat 25 Dec 2021 03:57:13 PM GMT.
    Package yum-utils-4.0.18-4.el8.noarch is already installed.
    Dependencies resolved.
    ===================================================================================================================================================================================
     Package                                            Architecture                     Version                                     Repository                                   Size
    ===================================================================================================================================================================================
    Upgrading:
     dnf-plugins-core                                   noarch                           4.0.21-3.0.1.el8                            ol8_baseos_latest                            70 k
     python3-dnf-plugins-core                           noarch                           4.0.21-3.0.1.el8                            ol8_baseos_latest                           234 k
     yum-utils                                          noarch                           4.0.21-3.0.1.el8                            ol8_baseos_latest                            72 k

    Transaction Summary
    ===================================================================================================================================================================================
    Upgrade  3 Packages

    Total download size: 377 k
    Is this ok [y/N]: y
    Downloading Packages:
    (1/3): yum-utils-4.0.21-3.0.1.el8.noarch.rpm                                                                                                       499 kB/s |  72 kB     00:00    
    (2/3): dnf-plugins-core-4.0.21-3.0.1.el8.noarch.rpm                                                                                                455 kB/s |  70 kB     00:00    
    (3/3): python3-dnf-plugins-core-4.0.21-3.0.1.el8.noarch.rpm                                                                                        1.2 MB/s | 234 kB     00:00    
    -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    Total                                                                                                                                              1.8 MB/s | 377 kB     00:00     
    Running transaction check
    Transaction check succeeded.
    Running transaction test
    Transaction test succeeded.
    Running transaction
      Preparing        :                                                                                                                                                           1/1 
      Upgrading        : python3-dnf-plugins-core-4.0.21-3.0.1.el8.noarch                                                                                                          1/6 
      Upgrading        : dnf-plugins-core-4.0.21-3.0.1.el8.noarch                                                                                                                  2/6 
      Upgrading        : yum-utils-4.0.21-3.0.1.el8.noarch                                                                                                                         3/6 
      Cleanup          : yum-utils-4.0.18-4.el8.noarch                                                                                                                             4/6 
      Cleanup          : dnf-plugins-core-4.0.18-4.el8.noarch                                                                                                                      5/6 
      Cleanup          : python3-dnf-plugins-core-4.0.18-4.el8.noarch                                                                                                              6/6 
      Running scriptlet: python3-dnf-plugins-core-4.0.18-4.el8.noarch                                                                                                              6/6 
      Verifying        : dnf-plugins-core-4.0.21-3.0.1.el8.noarch                                                                                                                  1/6 
      Verifying        : dnf-plugins-core-4.0.18-4.el8.noarch                                                                                                                      2/6 
      Verifying        : python3-dnf-plugins-core-4.0.21-3.0.1.el8.noarch                                                                                                          3/6 
      Verifying        : python3-dnf-plugins-core-4.0.18-4.el8.noarch                                                                                                              4/6 
      Verifying        : yum-utils-4.0.21-3.0.1.el8.noarch                                                                                                                         5/6 
      Verifying        : yum-utils-4.0.18-4.el8.noarch                                                                                                                             6/6 

    Upgraded:
      dnf-plugins-core-4.0.21-3.0.1.el8.noarch                   python3-dnf-plugins-core-4.0.21-3.0.1.el8.noarch                   yum-utils-4.0.21-3.0.1.el8.noarch                  

    Complete!
```
```
    sudo vim /etc/yum.repos.d/nginx.repo
    [nginx-stable]
    name=nginx stable repo
    baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
    gpgcheck=1
    enabled=1
    gpgkey=https://nginx.org/keys/nginx_signing.key
    module_hotfixes=true
```
```
yum repolist enabled nginx
```
2) Install NGINX.

```
    sudo yum install nginx
    nginx stable repo                                                                                                                                   89 kB/s |  35 kB     00:00    
    Dependencies resolved.
    ===================================================================================================================================================================================
     Package                              Architecture                          Version                                              Repository                                   Size
    ===================================================================================================================================================================================
    Installing:
     nginx                                x86_64                                1:1.20.2-1.el8.ngx                                   nginx-stable                                820 k

    Transaction Summary
    ===================================================================================================================================================================================
    Install  1 Package

    Total download size: 820 k
    Installed size: 2.8 M
    Is this ok [y/N]: y
    Downloading Packages:
    nginx-1.20.2-1.el8.ngx.x86_64.rpm                                                                                                                  2.7 MB/s | 820 kB     00:00    
    -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    Total                                                                                                                                              2.6 MB/s | 820 kB     00:00     
    warning: /var/cache/dnf/nginx-stable-614ef03fac352fea/packages/nginx-1.20.2-1.el8.ngx.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 7bd9bf62: NOKEY
    nginx stable repo                                                                                                                                  8.7 kB/s | 1.5 kB     00:00    
    Importing GPG key 0x7BD9BF62:
     Userid     : "nginx signing key <signing-key@nginx.com>"
     Fingerprint: 573B FD6B 3D8F BC64 1079 A6AB ABF5 BD82 7BD9 BF62
     From       : https://nginx.org/keys/nginx_signing.key
    Is this ok [y/N]: y
    Key imported successfully
    Running transaction check
    Transaction check succeeded.
    Running transaction test
    Transaction test succeeded.
    Running transaction
      Preparing        :                                                                                                                                                           1/1 
      Running scriptlet: nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                           1/1 
      Installing       : nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                           1/1 
      Running scriptlet: nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                           1/1 
    ----------------------------------------------------------------------

    Thanks for using nginx!

    Please find the official documentation for nginx here:
    * https://nginx.org/en/docs/

    Please subscribe to nginx-announce mailing list to get
    the most important news about nginx:
    * https://nginx.org/en/support.html

    Commercial subscriptions for nginx are available on:
    * https://nginx.com/products/

    ----------------------------------------------------------------------

      Verifying        : nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                           1/1 

    Installed:
      nginx-1:1.20.2-1.el8.ngx.x86_64                                                                                                                                                  

    Complete!
```
3) Check yum history and undo NGINX installation.
```
    sudo yum history
    ID     | Command line                                                                                                                 | Date and time    | Action(s)      | Altered
    -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
        23 | install nginx                                                                                                                | 2021-12-25 19:18 | Install        |    1 EE
        22 | install yum-utils                                                                                                            | 2021-12-25 19:10 | Upgrade        |    3  <
        21 | install tcpdump                                                                                                              | 2021-10-21 14:40 | Install        |    1 > 
        20 | install bind-utils                                                                                                           | 2021-10-19 15:10 | Install        |    8   
        19 | -y install telnet                                                                                                            | 2021-10-05 13:43 | Install        |    1   
        18 | install nmap                                                                                                                 | 2021-10-05 13:35 | Install        |    2   
        17 | upgrade                                                                                                                      | 2021-07-21 12:59 | Upgrade        |    1   
        16 | install xclip                                                                                                                | 2021-07-20 09:35 | Install        |    6   
        15 | install ansible                                                                                                              | 2021-07-16 14:58 | Install        |   16   
        14 | install oracle-epel-release-el8.x86_64                                                                                       | 2021-07-16 14:58 | Install        |    1   
        13 | install vim                                                                                                                  | 2021-07-14 08:13 | Install        |    4   
        12 | install git-all                                                                                                              | 2021-07-14 08:09 | Install        |   58   
        11 | install docker-ce docker-ce-cli containerd.io                                                                                | 2021-07-13 08:51 | Install        |   18   
        10 | install yum-utils                                                                                                            | 2021-07-13 08:46 | Install        |    1   
         9 | update                                                                                                                       | 2021-07-13 08:36 | E, I, U        |   71   
         8 | update                                                                                                                       | 2021-06-28 09:28 | E, I, O, U     |  264 EE
         7 | update                                                                                                                       | 2021-05-06 09:28 | I, U           |   60 EE
         6 | install rsyslog                                                                                                              | 2021-03-19 10:46 | Install        |    3   
         5 | update                                                                                                                       | 2021-03-19 10:33 | I, U           |  101 EE
         4 | install perl                                                                                                                 | 2021-01-19 12:30 | Install        |  152   
         3 | update                                                                                                                       | 2021-01-19 12:17 | Upgrade        |    5   
         2 | install open-vm-tools                                                                                                        | 2021-01-19 12:17 | Install        |   10   
         1 |                                                                                                                              | 2021-01-19 10:26 | Install        |  436 EE

```
4) Disable NGINX repository
```
    sudo yum-config-manager --disable nginx-stable
    [nik@dev-Kizhnyaev homework]$ cat /etc/yum.repos.d/nginx.repo
    [nginx-stable]
    name=nginx stable repo
    baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
    gpgcheck=1
    enabled=0
    gpgkey=https://nginx.org/keys/nginx_signing.key
    module_hotfixes=true
```
5) Remove sysstat package installed in the first task.
```
    sudo yum erase sysstat -y
    Dependencies resolved.
    ===================================================================================================================================================================================
     Package                                  Architecture                            Version                                           Repository                                Size
    ===================================================================================================================================================================================
    Removing:
     sysstat                                  x86_64                                  11.7.3-6.0.1.el8                                  @System                                  1.4 M

    Transaction Summary
    ===================================================================================================================================================================================
    Remove  1 Package

    Freed space: 1.4 M
    Running transaction check
    Transaction check succeeded.
    Running transaction test
    Transaction test succeeded.
    Running transaction
      Preparing        :                                                                                                                                                           1/1 
      Running scriptlet: sysstat-11.7.3-6.0.1.el8.x86_64                                                                                                                           1/1 
      Erasing          : sysstat-11.7.3-6.0.1.el8.x86_64                                                                                                                           1/1 
      Running scriptlet: sysstat-11.7.3-6.0.1.el8.x86_64                                                                                                                           1/1 
      Verifying        : sysstat-11.7.3-6.0.1.el8.x86_64                                                                                                                           1/1 

    Removed:
      sysstat-11.7.3-6.0.1.el8.x86_64                                                                                                                                                  

    Complete!
```
6) Install EPEL repository and get information about it.
```
    sudo yum install epel-release
    Loaded plugins: fastestmirror
    Loading mirror speeds from cached hostfile
     * base: mirrors.datahouse.ru
     * extras: mirror.axelname.ru
     * updates: mirror.axelname.ru
    Resolving Dependencies
    --> Running transaction check
    ---> Package epel-release.noarch 0:7-11 will be installed
    --> Finished Dependency Resolution

    Dependencies Resolved

    ===================================================================================================================================================================================================================
     Package                                                 Arch                                              Version                                         Repository                                         Size
    ===================================================================================================================================================================================================================
    Installing:
     epel-release                                            noarch                                            7-11                                            extras                                             15 k

    Transaction Summary
    ===================================================================================================================================================================================================================
    Install  1 Package

    Total download size: 15 k
    Installed size: 24 k
    Is this ok [y/d/N]: y
    Downloading packages:
    epel-release-7-11.noarch.rpm                                                                                                                                                                |  15 kB  00:00:01     
    Running transaction check
    Running transaction test
    Transaction test succeeded
    Running transaction
      Installing : epel-release-7-11.noarch                                                                                                                                                                        1/1 
      Verifying  : epel-release-7-11.noarch                                                                                                                                                                        1/1 

    Installed:
      epel-release.noarch 0:7-11                                                                                                                                                                                       

    Complete!
```
```
sudo yum repoinfo epel
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.datahouse.ru
 * epel: mirror.nsc.liu.se
 * extras: mirror.surf
 * updates: mirror.axelname.ru
Repo-id      : epel/x86_64
Repo-name    : Extra Packages for Enterprise Linux 7 - x86_64
Repo-status  : enabled
Repo-revision: 1640393346
Repo-pkgs    : 13 703
Repo-size    : 16 G
Repo-metalink: https://mirrors.fedoraproject.org/metalink?repo=epel-7&arch=x86_64
Repo-baseurl : http://mirror.nsc.liu.se/fedora-epel/7/x86_64/ (84 more)
Repo-expire  : 21 600 second(s) 
  Filter     : read-only:present
Repo-filename: /etc/yum.repos.d/epel.repo
```
7) Find how much packages provided exactly by EPEL repository.
```
Loading "fastestmirror" plugin
Config time: 0.008
Yum version: 3.4.3
Loading mirror speeds from cached hostfile
 * base: mirrors.datahouse.ru
 * epel: ftp.lysator.liu.se
 * extras: mirror.surf
 * updates: mirror.axelname.ru
Setting up Package Sacks
pkgsack time: 0.012
Repo-id      : epel/x86_64
Repo-name    : Extra Packages for Enterprise Linux 7 - x86_64
Repo-status  : enabled
Repo-revision: 1640393346
Repo-pkgs    : 13 703
Repo-size    : 16 G
Repo-metalink: https://mirrors.fedoraproject.org/metalink?repo=epel-7&arch=x86_64
Repo-baseurl : https://ftp.lysator.liu.se/pub/epel/7/x86_64/ (84 more)
Repo-expire  : 21 600 second(s) 
  Filter     : read-only:present
Repo-filename: /etc/yum.repos.d/epel.repo

repolist: 13 703
```
8) Install ncdu package from EPEL repo.
```
    sudo yum install ncdu -y
    Last metadata expiration check: 3:41:43 ago on Sat 25 Dec 2021 03:57:13 PM GMT.
    Dependencies resolved.
    ===================================================================================================================================================================================
     Package                              Architecture                           Version                                      Repository                                          Size
    ===================================================================================================================================================================================
    Installing:
     ncdu                                 x86_64                                 1.16-1.el8                                   ol8_developer_EPEL                                  60 k

    Transaction Summary
    ===================================================================================================================================================================================
    Install  1 Package

    Total download size: 60 k
    Installed size: 98 k
    Downloading Packages:
    ncdu-1.16-1.el8.x86_64.rpm                                                                                                                         583 kB/s |  60 kB     00:00    
    -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    Total                                                                                                                                              559 kB/s |  60 kB     00:00     
    Running transaction check
    Transaction check succeeded.
    Running transaction test
    Transaction test succeeded.
    Running transaction
      Preparing        :                                                                                                                                                           1/1 
      Installing       : ncdu-1.16-1.el8.x86_64                                                                                                                                    1/1 
      Running scriptlet: ncdu-1.16-1.el8.x86_64                                                                                                                                    1/1 
      Verifying        : ncdu-1.16-1.el8.x86_64                                                                                                                                    1/1 

    Installed:
      ncdu-1.16-1.el8.x86_64                                                                                                                                                           

    Complete!
```
