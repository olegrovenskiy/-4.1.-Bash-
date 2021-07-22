# -4.1.-Bash-

1. 

a=1
b=2
c=a+b
d=$a+$b
e=$(($a+$b))

с --> a+b
так как a, b, и с текстовые переменные

d --> 1+2

т.к. считывается значение записаное в a и b, как текстовая переменная

e --> 3

двойные скобки, арифметическое выражение, сначала вычисляется в первых скобках, а затем 
значение во вторых скобках

2.

while ((1==1)
do
curl https://localhost:4757
if (($? != 0))
then
date >> curl.log
# 
else
break

fi
done

3.

[root@mck-mbox-mig script]# cat 1.sh
#! /usr/bin/env bash


arr_ip=("http://192.168.0.1:80" "http://173.194.222.113:80" "http://87.250.250.242:80")

echo "" > log
for i in ${arr_ip[@]}
do
a=5
while (($a>0))
do
curl $i
if (($?==0))
then
echo $i   "service OK" >> log
else
echo $i   "service NOT OK" >> log
fi
a=$a-1
done
done


4.

#! /usr/bin/env bash


arr_ip=("http://192.168.0.1:80" "http://173.194.222.113:80" "http://87.250.250.242:80")

echo "" > log
while ((1==1))
do
for i in ${arr_ip[@]}
do
a=5
while (($a>0))
do
curl $i
if (($?==0))
then
echo $i   "service OK" >> log
else
echo $i   "service NOT OK" >> error
break
fi
a=$a-1
done
done
done

