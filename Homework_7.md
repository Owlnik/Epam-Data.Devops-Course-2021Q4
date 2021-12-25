
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
