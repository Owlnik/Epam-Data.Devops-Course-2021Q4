# Homework_3 by Nikita Kizhnyaev
## 1) awk
1) What is the most frequent browser?
```
awk '{ print $12 }' access.log | awk -F "/" '{ print $1 }'  | sed 's/"//g' | sort |  uniq -c | sort -g | tail -1 | awk '{ print $2 }'
```
2) Show number of requests per month for ip 216.244.66.230
```
awk ' $1 == "216.244.66.230"  { print $4 }'  access.log | awk -F "/" '{ print $2, $3 }' | awk -F ":" '{ print $1 }' | sort | uniq -c | awk '{ print $2, $3,"-", $1}'
```
3) Show total amount of data which server has provided for each unique ip
```
for i in `awk '{ print $1 }' access.log  | sort -g | uniq`; do  awk -v ip=$i '$1 == ip { x +=  $10 }END{ print x " bytes for " ip }' access.log; done;
```
## 2) sed
1) Change all browsers to "lynx"
```sed -e 's/Firefox/lynx/; s/Chrome/lynx/; s/Safari/lynx/; s/Opera/lynx/; s/OPR/lynx/; s/Edg/lynx/; s/Mobile/lynx/; s/Trident/lynx/; s/IEMobile/lynx/; s/curl/lynx/; s/PostmanRuntime/lynx/'```
2) Masquerade all ip addresses. Rewrite file.
