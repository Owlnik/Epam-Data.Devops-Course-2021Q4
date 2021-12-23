# Homework_1 Kizhnyaev Nikita
## 1.1) 
SSH to remotehost using username and password provided to you in Slack. Logout from remotehost.
 1) ```ssh Nikita_Kizhniaev@18.221.144.175```
    ```
       Nikita_Kizhniaev@18.221.144.175's password: 
    ```
    ``` ****```
    ```
      
       __|  __|_  )
       _|  (     /   Amazon Linux 2 AMI
      ___|\___|___|

    https://aws.amazon.com/amazon-linux-2/
    No packages needed for security; 4 packages available
    Run "sudo yum update" to apply all updates.
    [Nikita_Kizhniaev@ip-172-31-33-155 ~]$
    ```
    ```[Nikita_Kizhniaev@ip-172-31-33-155 ~]$ exit ```
## 1.2) 
    Generate new SSH key-pair on your localhost with name "hw-5" (keys should becreated in ~/.ssh folder).
    
    ```[nik@dev-Kizhnyaev homework]$ ssh-keygen -t ed25519 -f ~/.ssh/hw-5```
 ```
    Generating public/private ed25519 key pair.
    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 
    Your identification has been saved in /home/nik/.ssh/hw-5.
    Your public key has been saved in /home/nik/.ssh/hw-5.pub.
    The key fingerprint is:
    SHA256:dCtrKAbcfI1+7UmtPYOlPQKT3XdCe568Y5VqoivphdE nik@dev-Kizhnyaev
    The key's randomart image is:
    +--[ED25519 256]--+
    |                 |
    |                 |
    |        . .      |
    | . o   +.. .  .  |
    |  o o o.SE.. . ..|
    |   . o .*+..o +.+|
    |    o o.=+o=..o=o|
    |   . . =.o+==o =.|
    |      ...o*.++..o|
    +----[SHA256]-----+
```
## 1.3)
Set up key-based authentication, so that you can SSH to  remotehost  without password.

``` ssh-copy-id -i ~/.ssh/hw-5.pub Nikita_Kizhniaev@18.221.144.175  ```
```
    /usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/nik/.ssh/hw-5.pub"
    /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
    /usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
    Nikita_Kizhniaev@18.221.144.175's password: 

    Number of key(s) added: 1

    Now try logging into the machine, with:   "ssh 'Nikita_Kizhniaev@18.221.144.175'"
    and check to make sure that only the key(s) you wanted were added.
```
## 1.4)
SSH to remotehost without password. Log out from remotehost.

```ssh -i ./.ssh/hw-5 Nikita_Kizhniaev@18.221.144.175```
```Last login: Thu Dec 23 13:13:21 2021 from 46.243.180.245

       __|  __|_  )
       _|  (     /   Amazon Linux 2 AMI
      ___|\___|___|

  https://aws.amazon.com/amazon-linux-2/
  No packages needed for security; 4 packages available
  Run "sudo yum update" to apply all updates.
```
```[Nikita_Kizhniaev@ip-172-31-33-155 ~]$ exit```
```
  logout
  Connection to 18.221.144.175 closed.
```
## 1.5)
Create SSH config file, so that you can SSH to remotehost simply running `ssh remotehost` command. As a result, provide output of command `cat ~/.ssh/config`

``` vim ~/.ssh/config ```
``` 
  Host 18.221.144.175 
    PreferredAuthentications publickey
    IdentityFile /home/nik/.ssh/hw-5
    User Nikita_Kizhniaev
```
## 1.6)
Using command line utility (curl or telnet) verify that there are some webserver running on port 80 of webserver.  Notice that webserver has a private network IP, so you can access it only from the same network (when you are on remotehost that runs in the same private network). Log out from remotehost.

``` curl 172.31.45.237:80```
```
 <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd"><html><head>
 ...
```
## 1.7)
Using SSH setup port forwarding, so that you can reach  webserver from your localhost (choose any free local port you like).

``` ssh -L 8080:172.31.45.237:80 18.221.144.175 &```
## 1.8)
Like in 1.6, but on localhost using command line utility verify that localhost and port you have specified act like webserver, returning same result as in 1.6.

``` curl 127.1:8080 ```
```
  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd"><html><head>
  ...
```
## 2.1)
Imagine your localhost has been relocated to Havana. Change the time zone on the localhost to Havana and verify the time zone has been changed properly (may be multiple commands)

```sudo timedatectl set-timezone America/Havana```
```timedatectl status```
## 2.2)

