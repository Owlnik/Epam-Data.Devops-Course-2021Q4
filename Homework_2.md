# Homework_1 Kizhnyaev Nikita
## 1)
  Открыть инструкцию по пользованию приложением awk. Найти секцию про использование переменных окружения. Сохранить эту секцию в отдельный файл.
  1) ``` man awk |  sed "1502,1514 p" > testfile```
## 2)
  Написать скрипт, который создаёт файл "task2.txt" директорией выше своего местоположения. В случае ошибки текст ошибки записывается в err.log а пользователю выдаётся сообщение "Error."
  1) ```
     #!/bin/bash
     touch ../task2.txt 2>~/err.log
     if [$? != 0] then 
     echo "Error"
     fi
     ```
      Если файл уже существует, выдаётся одна ошибка, а если нет прав для его создания - другая.
   2) ```
      #!/bin/bash
      if [ -e ../task2.txt]
      echo "File exist" && exit
      fi 
      touch ../task2.txt 2>~/err.log
      if [$? = 1] then 
      echo "Permission denied"
      fi
      ```
## 3)
   1) Создать 2 файла: 1-й - текстовый с указанием абслютного пути до директории. 2-й - скрипт, который при выполнении выводит содержимое директории по указанному в первом файле.
   
     ```pwd > file1```
     
     ```
     #!/bin/bash
     input="file1"
     while read -r path
     do
     ls $path
     done < $input
     ```
   2) Скрипт выводит отдельно количество файлов и количество директорий.
  
     ```
     #!/bin/bash
     input="file1"
     while read -r path
     do
     echo directoryes
     ls -laAd $path | wc -l
     num_direct = ls -laAd $path | wc -l
     ls -laA $path  | wc -l - num_direct
     done < $input
     ```
  3) Скрипт принимает любое количество записей в первом файле и обрабатывает их последовательно.

   ```
     #!/bin/bash
     input="file1.txt"
     while read -r path
     do
     echo directoryes
     ls -laAd $path | wc -l
     num_direct = ls -laAd $path | wc -l
     ls -laA $path  | wc -l - $num_direct
     done < $input
     ```
