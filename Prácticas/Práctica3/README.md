#Práctica 3


0. ##Estructura del entorno virtual.

	**Maquina de balanceo:** *192.168.1.5*



1. ###Instalar nginx en Ubuntu Server.

	**Importando la clave:**

	*Nos posicionamos en el directorio tmp donde descargaremos la clave del repositorio*

	`$> cd /tmp/`

	*Obtenemos las clave del repositorio*

	`$> wget http://nginx.org/keys/nginx_signing.key`

	*La añadimos a nuestra lista de claves*

	`$> apt-key add /tmp/nginx_signing.key`

	*Ya podemos eliminarla de tmp*

	`$> rm -f /tmp/nginx_signing.key`

	
	![Imagen 1](Capturas/1__.png "Práctica 3.1")



	**Añadiendo el repositorio, editando el fichero /etc/apt/sources.list**

	`$> echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list`
	
	`$> echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list`

	![Imagen 1.2](Capturas/2__.png "Práctica 3.1")



	**Instalando el paquete del nginx:**

	`$> apt-get update`
	
	![Imagen 1.3](Capturas/3__.png "Práctica 3.1")

	`$> apt-get install nginx`
	
	![Imagen 1.4](Capturas/3.1__.png "Práctica 3.1")

	![Imagen 1.5](Capturas/3.2__.png "Práctica 3.1")

	*sí ocurriera este error es debido a que el puerto 80 esta ocupado.*

	*En este caso por apache.*

	*Podemos desinstalarlo usando:*
	
	`$> sudo service apache2 stop`

	`$> sudo apt-get purge apache2*`

	`$> sudo apt-get autoremove`

	`$> sudo rm -Rf /etc/apache2 /usr/lib/apache2 /usr/include/apache2`
	
	*Levantamos el servicio: *

	`$> sudo service nginx start`



2. ###Balanceo de carga usando nginx.

	**Configurando nginx**
	
	`$> sudo nano /etc/nginx/conf.d/default.conf`
	
	![Imagen 1.6](Capturas/4__.png "Práctica 3.2")

	**Configurando cargas personalizadas**	

	*Basta con añadir la carga deseada* **weight** *a cada servidor.*
	
	![Imagen 1.8](Capturas/4.1__.png "Práctica 3.2")

	**Configurando el trafico para que guarde fidelidad**	

	*Basta con añadir la directiva* **ip_hash** *al definir el upstream.*
	
	![Imagen 1.9](Capturas/4.2__.png "Práctica 3.2")
		
	**Configurando nginx para que use** *keepalive*	

	*Basta con añadir la directiva* **keepalive** *y su tiempo de vida al definir el upstream.*
	
	![Imagen 2](Capturas/4.3__.png "Práctica 3.2")
	
	**Probando nginx**
	
	`$> curl http://192.168.1.5`

	![Imagen 1.7](Capturas/4.4__.png "Práctica 3.2")

	**round-robin** 

	![Imagen 2.4](Capturas/4.5__.png "Práctica 3.2")

	**Usando ponderación**

	![Imagen 2.5](Capturas/4.6__.png "Práctica 3.2")



3. ###Balanceo de carga usando haproxy.
	
	**Instalando haproxy**
	
	`$> sudo apt-get install haproxy joe`

	![Imagen 2.1](Capturas/5__.png "Práctica 3.3")

	**Configuración básica de haproxy como balanceador de carga**

	![Imagen 2.2](Capturas/5.1__.png "Práctica 3.3")
	
	**Comprobando el funcionamiento del balanceador**
	
	*Si tenemos instalado nginx debemos tirar el servicio:*

	`$> service nginx stop`	

	*Una vez configurado relanzamos el servicio:*
	
	`$> sudo /usr/sbin/haproxy -f /etc/haproxy/haproxy.cfg`

	![Imagen 2.3](Capturas/5.2__.png "Práctica 3.3")

	*Lo probamos mediante:*
	
	`$> curl http://192.168.1.5`

	`$> curl http://192.168.1.5`
	
	**round-robin** 

	![Imagen 2.4](Capturas/5.3__.png "Práctica 3.3")

	**Usando ponderación**

	![Imagen 2.5](Capturas/5.4__.png "Práctica 3.3")



**Autores:** *Alejandro Rodríguez López y Antonio Cordonie Campos*	
		
	


