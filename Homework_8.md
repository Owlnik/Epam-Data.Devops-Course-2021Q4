# Homework_8
## particion
Imagine you was asked to add new partition to your host for backup purposes. To simulate appearance of new physical disk in your server, please create new disk in Virtual Box (5 GB) and attach it to your virtual machine.
Also imagine your system started experiencing RAM leak in one of the applications, thus while developers try to debug and fix it, you need to mitigate OutOfMemory errors; you will do it by adding some swap space.
/dev/sdc - 5GB disk, that you just attached to the VM (in your case it may appear as /dev/sdb, /dev/sdc or other, it doesn't matter)
1.1) Create a 2GB   !!! GPT !!!   partition on /dev/sdc of type "Linux filesystem" (means all the following partitions created in the following steps on /dev/sdc will be GPT as well)
```
    sudo parted /dev/sdb
    GNU Parted 3.2
    Using /dev/sdb
    Welcome to GNU Parted! Type 'help' to view a list of commands.
```
```
    (parted) p                                                                
    Error: /dev/sdb: unrecognised disk label
    Model: VMware Virtual disk (scsi)                                         
    Disk /dev/sdb: 5369MB
    Sector size (logical/physical): 512B/512B
    Partition Table: unknown
    Disk Flags: 
```
  sudo parted -a optimal /dev/sdb mkpart primary 0% 2048MB
  You may need to update /etc/fstab.
  sudo parted /dev/sdb 
  GNU Parted 3.2
  Using /dev/sdb
  Welcome to GNU Parted! Type 'help' to view a list of commands.
  (parted) p                                                                
  Model: VMware Virtual disk (scsi)
  Disk /dev/sdb: 5369MB
  Sector size (logical/physical): 512B/512B
  Partition Table: gpt
  Disk Flags: 

  Number  Start   End     Size    File system  Name     Flags
   1      1049kB  2048MB  2047MB               primary

  (parted) q     
```
1.2) Create a 512MB partition on /dev/sdc of type "Linux swap"
```
    sudo fdisk /dev/sdb
  
    Welcome to fdisk (util-linux 2.32.1).
    Changes will remain in memory only, until you decide to write them.
    Be careful before using the write command.

    Command (m for help): p 
    Disk /dev/sdb: 5 GiB, 5368709120 bytes, 10485760 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: gpt
    Disk identifier: FFE1C79D-828F-4BBF-92C0-86691BF650E3

    Device     Start     End Sectors  Size Type
    /dev/sdb1   2048 3999743 3997696  1.9G Linux filesystem

    Command (m for help): n
    Partition number (2-128, default 2): 2
    First sector (3999744-10485726, default 3999744): 
    Last sector, +sectors or +size{K,M,G,T,P} (3999744-10485726, default 10485726): +512K

    Created a new partition 2 of type 'Linux filesystem' and of size 512 KiB.

    Command (m for help): t 2
    Partition number (1,2, default 2): 2
    Partition type (type L to list all types): l
      1 EFI System                     C12A7328-F81F-11D2-BA4B-00A0C93EC93B
      2 MBR partition scheme           024DEE41-33E7-11D3-9D69-0008C781F39F
      3 Intel Fast Flash               D3BFE2DE-3DAF-11DF-BA40-E3A556D89593
      4 BIOS boot                      21686148-6449-6E6F-744E-656564454649
      5 Sony boot partition            F4019732-066E-4E12-8273-346C5641494F
      6 Lenovo boot partition          BFBFAFE7-A34F-448A-9A5B-6213EB736C22
      7 PowerPC PReP boot              9E1A2D38-C612-4316-AA26-8B49521E5A8B
      8 ONIE boot                      7412F7D5-A156-4B13-81DC-867174929325
      9 ONIE config                    D4E6E2CD-4469-46F3-B5CB-1BFF57AFC149
     10 Microsoft reserved             E3C9E316-0B5C-4DB8-817D-F92DF00215AE
     11 Microsoft basic data           EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
     12 Microsoft LDM metadata         5808C8AA-7E8F-42E0-85D2-E1E90434CFB3
     13 Microsoft LDM data             AF9B60A0-1431-4F62-BC68-3311714A69AD
     14 Windows recovery environment   DE94BBA4-06D1-4D40-A16A-BFD50179D6AC
     15 IBM General Parallel Fs        37AFFC90-EF7D-4E96-91C3-2D7AE055B174
     16 Microsoft Storage Spaces       E75CAF8F-F680-4CEE-AFA3-B001E56EFC2D
     17 HP-UX data                     75894C1E-3AEB-11D3-B7C1-7B03A0000000
     18 HP-UX service                  E2A1E728-32E3-11D6-A682-7B03A0000000
     19 Linux swap                     0657FD6D-A4AB-43C4-84E5-0933C84B4F4F
     20 Linux filesystem               0FC63DAF-8483-4772-8E79-3D69D8477DE4
     21 Linux server data              3B8F8425-20E0-4F3B-907F-1A25A76F98E8
     22 Linux root (x86)               44479540-F297-41B2-9AF7-D131D5F0458A
     23 Linux root (ARM)               69DAD710-2CE4-4E3C-B16C-21A1D49ABED3
     24 Linux root (x86-64)            4F68BCE3-E8CD-4DB1-96E7-FBCAF984B709
     25 Linux root (ARM-64)            B921B045-1DF0-41C3-AF44-4C6F280D3FAE
     26 Linux root  (IA-64)             993D8D3D-F80E-4225-855A-9DAF8ED7EA97
     27 Linux reserved                 8DA63339-0007-60C0-C436-083AC8230908
     28 Linux home                     933AC7E1-2EB4-4F13-B844-0E14E2AEF915
     29 Linux RAID                     A19D880F-05FC-4D3B-A006-743F0F84911E
     30 Linux extended boot            BC13C2FF-59E6-4262-A352-B275FD6F7172
     31 Linux LVM                      E6D6D379-F507-44C2-A23C-238F2A3DF928
     32 FreeBSD data                   516E7CB4-6ECF-11D6-8FF8-00022D09712B
     33 FreeBSD boot                   83BD6B9D-7F41-11DC-BE0B-001560B84F0F
     34 FreeBSD swap                   516E7CB5-6ECF-11D6-8FF8-00022D09712B
     35 FreeBSD UFS                    516E7CB6-6ECF-11D6-8FF8-00022D09712B
     36 FreeBSD ZFS                    516E7CBA-6ECF-11D6-8FF8-00022D09712B

    Partition type (type L to list all types): 
    Partition type (type L to list all types): 19

    Changed type of partition 'Linux filesystem' to 'Linux swap'.

    Command (m for help): w 
    The partition table has been altered.
    Calling ioctl() to re-read partition table.
    Syncing disks.
```
1.3)Format the 2GB partition with an XFS file system
``` 
    sudo mkfs.xfs /dev/sdb1
    meta-data=/dev/sdb1              isize=512    agcount=4, agsize=124928 blks
             =                       sectsz=512   attr=2, projid32bit=1
             =                       crc=1        finobt=1, sparse=1, rmapbt=0
             =                       reflink=1
    data     =                       bsize=4096   blocks=499712, imaxpct=25
             =                       sunit=0      swidth=0 blks
    naming   =version 2              bsize=4096   ascii-ci=0, ftype=1
    log      =internal log           bsize=4096   blocks=2560, version=2
             =                       sectsz=512   sunit=0 blks, lazy-count=1
    realtime =none                   extsz=4096   blocks=0, rtextents=0
    lsblk -f
    NAME        FSTYPE      LABEL UUID                                   MOUNTPOINT
    sda                                                                  
    ├─sda1      vfat              3A44-1B61                              /boot/efi
    ├─sda2      xfs               2f3fc09a-f87a-40bb-ad8f-7804e444f8a8   /boot
    └─sda3      LVM2_member       jRaex5-jeFe-uKSQ-V9N5-hi1E-oNze-0sg1E3 
      ├─ol-root xfs               e1b5755c-ebdd-4a3d-807f-a70cbce509b8   /
      └─ol-swap swap              1e97a3f7-8ad2-49ea-906e-369107112e0e   [SWAP]
    sdb                                                                  
    ├─sdb1      xfs               a2473442-2c59-40b4-9934-7793335c8deb   
    └─sdb2                                                               
    sr0                                                                  
```
1.4) Initialize 512MB partition as swap space

```
    sudo mkswap -f /dev/sdb2
    Setting up swapspace version 1, size = 508 KiB (520192 bytes)
    no label, UUID=f742f795-c123-4a5a-93ac-374631883419
```
```
    swapon /dev/sdb2
```
```
    lsblk -f
    NAME        FSTYPE      LABEL UUID                                   MOUNTPOINT
    sda                                                                  
    ├─sda1      vfat              3A44-1B61                              /boot/efi
    ├─sda2      xfs               2f3fc09a-f87a-40bb-ad8f-7804e444f8a8   /boot
    └─sda3      LVM2_member       jRaex5-jeFe-uKSQ-V9N5-hi1E-oNze-0sg1E3 
      ├─ol-root xfs               e1b5755c-ebdd-4a3d-807f-a70cbce509b8   /
      └─ol-swap swap              1e97a3f7-8ad2-49ea-906e-369107112e0e   [SWAP]
    sdb                                                                  
    ├─sdb1      xfs               a2473442-2c59-40b4-9934-7793335c8deb   
    └─sdb2      swap              f742f795-c123-4a5a-93ac-374631883419   [SWAP]
    sr0                                                                  
```
1.5 Configure the newly created XFS file system to persistently mount at /backup
``` sudo mkdir /backup```
```sudo mount /dev/sdb1 /backup```
```
      df -hT
    Filesystem          Type      Size  Used Avail Use% Mounted on
    devtmpfs            devtmpfs  1.9G     0  1.9G   0% /dev
    tmpfs               tmpfs     1.9G  4.0K  1.9G   1% /dev/shm
    tmpfs               tmpfs     1.9G   25M  1.8G   2% /run
    tmpfs               tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
    /dev/mapper/ol-root xfs        38G   11G   27G  29% /
    /dev/sda2           xfs      1014M  300M  715M  30% /boot
    /dev/sda1           vfat      599M  5.1M  594M   1% /boot/efi
    tmpfs               tmpfs     374M     0  374M   0% /run/user/1000
    /dev/sdb1           xfs       1.9G   46M  1.9G   3% /backup
```
