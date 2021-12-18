# Homework_5 by Kizhnyaev Nikita
## Processes
1) ```sleep 100000000 &```
2) ```sleep 100000000000 &```
3) ```sleep 100000000 &```
4) ```kill -SIGSTOP 554957```
5) ```kill -SIGSTOP %2```
6) ```pkill -SIGSTOP sleep```
7) ```kill -9 556052```
8) ```pkill -SIGCOUNT sleep```
9) ```kill  -SIGCOUNT %2```
10) ```kill -9 %2```
11) ```kill -9 556052```
## systemd
1) demon1.service
```
    [Unit]
      Description=echo_1totmp
 
    [Service]
      ExecStart=/bin/bash /home/nik/file1.sh
      Type=idle
      KillMode=process
 
      SyslogIdentifier=echo1to_tmp
      SyslogFacility=daemon
 
      Restart=on-failure
 
    [Install]
      WantedBy=multiuser.target
```
 file1.sh
```
     #!/bin/bash
     sleep 10
     echo 1 > /tmp/homework
```
demon2.service
 ```
   [Unit]
     Description=echo_2totmp
 
   [Service]
     ExecStart=/bin/bash /home/nik/file2.sh
     Type=oneshot
 
   [Install]
     WantedBy=multiuser.target
 ```
  file2.sh
 ```
    #!/bin/bash
    echo 2 > /tmp/homework
 ```
 2) demon2.service
```
    [Unit]
     Description=echo_2totmp
     After=demon1
     
   [Service]
     ExecStart=/bin/bash /home/nik/file2.sh
     Type=oneshot
 
   [Install]
     WantedBy=multiuser.target
```
3) demon2.timer
```
    [Unit]
      Description=timer for demon 2 
     
    [Timer]
      OnCalendar=2019-01-01 00:00:00
    
    [Install]
      WantedBy=multiuser.target
```
4) ``` sudo systemctl demon1 start ```
5) ``` sudo systemctl demon2.service start ```
6) ``` sudo systemctl demon2.timer start ```
7) ``` sudo systemctl demon2.service start ```
8) ``` sudo systemctl status demon1 ```
9) ``` sudo systemctl status demon2.service ```
10) ``` sudo systemctl status demon2.timer ```
11) ``` less /tmp/homework ```
12)  ``` sudo systemctl stop demon1 ```
13) ``` sudo systemctl stop demon2.service ```
14) ``` sudo systemctl stop demon2.timer ```
## cron/anacron
1) testscript.sh
```
      #!/bin/bash
       echo Hello > /opt/hello
```
2) ```echo @daily 2 example.daily /bin/bash /home/nik/testscript.sh >> etc/anacrontab```
3) ``` crontab -e```
4) ```@reboot sleep 60 && /bin/bash /home/nik/testscript.sh```
## lsof
1) ``` sleep 3600  1>file1 2>file2 & ```
2) ``` lsof -p 557825```
3) ``` lsof -i ```
