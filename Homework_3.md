# Homework_3 by Nikita Kizhnyaev
## 1)
1) What is the most frequent browser?
```
awk '{ print $12 }' access.log | awk -F "/" '{ print $1 }'  | sed 's/"//g' | sort |  uniq -c | sort -g | tail -1 | awk '{ print $2 }'
```
