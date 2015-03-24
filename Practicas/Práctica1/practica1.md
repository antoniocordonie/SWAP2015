#Práctica1

1. **Resultado de la ejecución de la orden** *apache2 -v*:
	```
	Last login: Tue Mar  3 16:30:02 2015 from 
	user@ubuntuServer-1:~$ apache2 -v
	Server version: Apache/2.2.22 (Ubuntu)
	Server built:   Jul 22 2014 14:37:02
	```

2. **Resultado de la ejecución de la orden** *ps aux | grep apache*:
	```
	user@ubuntuServer-1:~$ ps aux | grep apache
	root      1224  0.0  0.6  34044  6900 ?        Ss   16:13   0:00 /usr/sbin/apache2 -k start
	www-data  1282  0.0  0.3  34068  3768 ?        S    16:13   0:00 /usr/sbin/apache2 -k start
	www-data  1283  0.0  0.3  34068  3768 ?        S    16:13   0:00 /usr/sbin/apache2 -k start
	www-data  1284  0.0  0.4  34100  4448 ?        S    16:13   0:00 /usr/sbin/apache2 -k start
	www-data  1285  0.0  0.4  34100  4448 ?        S    16:13   0:00 /usr/sbin/apache2 -k start
	www-data  1286  0.0  0.4  34116  4264 ?        S    16:13   0:00 /usr/sbin/apache2 -k start
	user      2580  0.0  0.0   4412   824 pts/0    S+   16:46   0:00 grep --color=auto apache
	user@ubuntuServer-1:~$
	```
	![Imagen 1](1__.png "Práctica 1")
