# Homework_4 by Kizhnyaev Nikita
## Task 1
1) Создайте группу sales с GID 4000 и пользователей bob, alice, 
eve c основной группой sales. 
Измените пользователям пароли.
Все новые аккаунты должны обязательно менять свои пароли 
каждый 30 дней.
Новые аккаунты группы sales должны истечь по окончанию 90 
дней срока, а bob должен изменять его пароль каждые 15 
дней.
Дополнительно:
Заставьте пользователей сменить пароль после первого 
логина.
2) ```groupadd --gid 4000 sales```
3) ```useradd --expiredate `date --date="90 days" +%Y-%m-%d` -g 4000 -m eve```
4) ```useradd --expiredate `date --date="90 days" +%Y-%m-%d` -g 4000 -m alice```
5) ```useradd --expiredate `date --date="90 days" +%Y-%m-%d` -g 4000 -m bob```
6) ```passwd bob```
7) ```passwd alice```
8) ```passwd eve```
9) ```chage -M 15 -d 0 bob```
10) ```chage -M 30 -d 0 alice```
11) ```chage -M 30  -d 0 eve```
## Task 2
1) Создайте трёх пользователей glen, antony, lesly.
У вас должна быть директория /home/students, где эти три 
пользователя могут работать совместно с файлами.
Должен быть возможен только пользовательский и групповой 
доступ, создание и удаление файлов в /home/students. 
Файлы, созданные в этой директории, должны автоматически 
присваиваться группе студентов students.
2) ``` groupadd --gid students ```
3) ```useradd -m -g students glen ```
4) ```useradd -m -g students antony```
5) ```useradd -m -g students lesly```
5) ```mkdir /home/students```
6) ```chgrp students /home/students```
7) ```chmod 2775 /home/students```
## Task 3
1) Ваша задача - завершить настройку директории общего 
доступа. 
Директория и всё её содержимое должно принадлежать группе
bakerstreet, при этом файлы должны обновляться для чтения 
и записи для владельца и группы (bakerstreet). У других 
пользователей не должно быть никаких разрешений. 
Вам также необходимо предоставить доступы на чтение и 
запись для группы scotlandyard, за исключением Jones, 
который может только читать документы.
Убедитесь, что ваша настройка применима к существующим и 
будущим файлам. После установки всех разрешений в 
директории проверьте от каждого пользователя все его 
возможные доступы.
Используйте команды: touch, mkdir, chgrp, chmod, getfacl, setfacl
и другие. 
Создайте общую директорию /share/cases.
Создайте группу bakerstreet с пользователями holmes, 
watson.
Создайте группу scotlandyard с пользователями lestrade, 
gregson, jones.
Задайте всем пользователям безопасные пароли.
Предварительный шаг:
От суперпользователя создайте папку /share/cases и создайте 
внутри 2 файла murders.txt и moriarty.txt.
Ваша задача - завершить настройку директории общего 
доступа. 
Директория и всё её содержимое должно принадлежать группе
bakerstreet, при этом файлы должны обновляться для чтения 
и записи для владельца и группы (bakerstreet). У других 
пользователей не должно быть никаких разрешений. 
Вам также необходимо предоставить доступы на чтение и 
запись для группы scotlandyard, за исключением Jones, 
который может только читать документы.
Убедитесь, что ваша настройка применима к существующим и 
будущим файлам. После установки всех разрешений в 
директории проверьте от каждого пользователя все его 
возможные доступы.
Используйте команды: touch, mkdir, chgrp, chmod, getfacl, setfacl
и другие. 
Создайте общую директорию /share/cases.
Создайте группу bakerstreet с пользователями holmes, 
watson.
Создайте группу scotlandyard с пользователями lestrade, 
gregson, jones.
Задайте всем пользователям безопасные пароли.
Предварительный шаг:
От суперпользователя создайте папку /share/cases и создайте 
внутри 2 файла murders.txt и moriarty.txt.
2) ```sudo mkdir -p /share/cases```
3) ```sudo touch /share/cases/{murders,moriarty}.txt```
4) ```groupadd bakerstreet```
5) ```groupadd scotlandyard```
6) ```useradd -m -g bakerstreet holmes```
7) ```useradd -m -g bakerstreet watson```
8) ```useradd -m -g scotlandyard lestrade```
9) ```useradd -m -g scotlandyard gregson```
10) ```useradd -m -g scotlandyard jones```
11) ```passwd holmes```
12) ```passwd watson```
13) ```passwd lestrade```
14) ```passwd gregson```
15) ```passwd jones```
16) ```chgrp -R /share/cases```
17) ```setfacl -R -m g:bakerstreet:rwx,g:scotlandyard:rw,u:jones:r--,m:--- /share/cases```
18) ```chmod g+s /share/cases```
