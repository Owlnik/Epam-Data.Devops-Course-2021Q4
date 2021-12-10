# Homework_3 by Nikita Kizhnyaev
## 1)
1) What is the most frequent browser?
```
awk '{ print $12 }' access.log | awk -F "/" '{ print $1 }'  | sed 's/"//g' | sort |  uniq -c | sort -g | tail -1 | awk '{ print $2 }'
```
2) Show number of requests per month for ip 216.244.66.230
```
awk ' $1 == "216.244.66.230"  { print $4 }'  access.log | awk -F "/" '{ print $2, $3 }' | awk -F ":" '{ print $1 }' | sort | uniq -c | awk '{ print $2, $3,"-", $1}'
```
3) Show total amount of data which server has provided for each unique ip
