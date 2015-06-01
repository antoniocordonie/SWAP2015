#Práctica 5


1. ###Estructura del entorno virtual.

	**Maquina1:** *192.168.1.10*

	**Maquina2:** *192.168.1.20*

	**Maquina de balanceo(Ngingx) :** *192.168.1.30*

	**Maquina de balanceo(HAProxy):** *192.168.1.30*


	##El software para la realización de los tests de estrés de la granja web ha sido Apache benchmark y Siege.

*Se han realizado un total de 10 repeticiones contra la Máquina1, otras 10 repeticiones contra el balanceador de carga con Ngingx y otras 10 repeticiones contra el balanceador de carga con HAProxy, primeramente con Apache Benchmark y después con Siege.*


2. ###Apache Benchmark:


	*Tabla de resultados Apache Benchmark contra la Máquina1*
	
	`ab -n 1000 -c 10 http://192.168.1.10/script.php`

	![Imagen 1](Capturas/4__1.png "Práctica 4.1")

	##Podemos observar en la siguiente captura como la Máquina1 tiene el uso de CPU al 99,7% y la Máquina2 al 0,0%
	
	![Imagen 2](Capturas/AB-contra-UbuntuServer1.png "Práctica 4.1")



	*Tabla de resultados Apache Benchmark contra el Balanceador con HAProxy*
	
	`ab -n 1000 -c 10 http://192.168.1.30/script.php`

	![Imagen 3](Capturas/4__2.png "Práctica 4.1")


	*Tabla de resultados Apache Benchmark contra el Balanceador con Ngingx*
	
	`ab -n 1000 -c 10 http://192.168.1.30/script.php`

	![Imagen 4](Capturas/4__3.png "Práctica 4.1")


	*Gráfica de resultados obtenidos en los 3 benchmarks con AB*

	![Imagen 5](Capturas/4__7.png "Práctica 4.1")


3. ###Siege:

	*Tabla de resultados Siege contra la Máquina1*
	
	`siege -b -t60S -v http://192.168.1.10/script.php`

	![Imagen 1](Capturas/4__4.png "Práctica 4.2")


	*Tabla de resultados Siege contra el balanceador de carga con HAProxy*
	
	`siege -b -t60S -v http://192.168.1.30/script.php`

	![Imagen 2](Capturas/4__5.png "Práctica 4.2")


	*Tabla de resultados Siege contra el balanceador de carga con Ngingx*
	
	`siege -b -t60S -v http://192.168.1.30/script.php`

	![Imagen 3](Capturas/4__6.png "Práctica 4.2")


	*Gráfica de resultados obtenidos en los 3 benchmarks con Siege*

	![Imagen 4](Capturas/4__8.png "Práctica 4.2")



**Autores:** *Alejandro Rodríguez López y Antonio Cordonie Campos*	
		
	


