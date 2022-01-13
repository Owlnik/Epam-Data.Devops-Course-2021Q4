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
``` sudo ln -s /usr/local/hadoop/current /opt/hadoop-3.1.2/ ```
