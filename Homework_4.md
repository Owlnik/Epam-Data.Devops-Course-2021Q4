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
