
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
