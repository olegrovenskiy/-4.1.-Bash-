# -4.1.-Bash- Домашняя работа
==============================================================

## 1. Задание 1.

Есть скрипт:
	```bash
	a=1
	b=2
	c=a+b
	d=$a+$b
	e=$(($a+$b))
	```
	* Какие значения переменным c,d,e будут присвоены?
	* Почему?

с --> будет присвоено a+b
так как a, b, и с текстовые переменные и мы получаем просто текс 

d --> будет присвоено 1+2

т.к. считывается значение записаное в a и b, и дадее ти значения
как текстовые переменные

e --> будет присвоено 3

двойные скобки в уоторых выполняется арифмитическое выражение, таким образом сначала вычисляется значение  в первых скобках, а затем 
значение во вторых скобках

## 2. Задание 2

Изменённый скрипт ниже:

	while ((1==1)  
	do  
	curl https://localhost:4757  
	if (($? != 0))  
	then  
	date >> curl.log  
	  
	else  
	break  
	  
	fi  
	done  


был добавлен оператор выхода из цикла, если сервис стал доступен

## 3. Задание 3

Необходимо написать скрипт, который проверяет доступность трёх IP: 192.168.0.1, 173.194.222.113, 87.250.250.242 по 80 порту и записывает результат в файл log. Проверять доступность необходимо пять раз для каждого узла.

Текст скрипта ниже:

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
 
 Скрмпт был протестирован на рабочем сервере с рабочими адресами.
 
  
## 4. Задание

Изменённый скрипт:

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
