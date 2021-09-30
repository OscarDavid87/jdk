# Instalación de JDK


## ¿Cómo instalar Java en Ubuntu desde repositorios?

Actualizamos el sistema con:

```
  sudo apt-get update
```

e instalamos Java con este comando:

```
  sudo apt-get install default-jdk
```

<img src="ImagenesJDK/1.png" alt="1">

En esta imagen vemos como se ejecutan los comandos anteriormente comentados. Podemos ver la ejecución de la instalación, una vez finalizada pasamos al siguiente comando 



comprobamos que tenemos instalado Java en nuestro sistema solo debemos de ejecutar:
```
  java --version
```


<img src="ImagenesJDK/java - version 1.1.png" alt="java - version 1.1">






## ¿Cómo instalar una versión específica de Java?

Para instalar Ubuntu Java Open JDK utilizamos los siguientes comandos:
Para OpenJDK 11, 9 y 8 respectivamente:

   - 11
   ```
   sudo apt install openjdk-11-jdk
   ```
    - 9
   ```
   sudo apt install openjdk-9-jdk
   ```
    - 8
   ```
   sudo apt install openjdk-8-jdk
   ```


<img src="ImagenesJDK/2.2.png" alt="2.2">

Vemos que al intentar la versión 9 nos da un fallo. Pasamos directamente a instalar la versión 8.

<img src="ImagenesJDK/2.3.png" alt="2.3">

La versión que se debe de trabajar es la versión 8. Para ello verificaremos la versión de java que se esta ejecutando con la sentencia:

```console
  java --version
```

<img src="ImagenesJDK/3.1.png" alt="3.1">



Efectivamente vemos que tenemos instalada la versión 11.0.11, como no se ejecuta la versión 8 que la que queremos debemos configurar las variables de entorno


## Configuración de las variables de entorno

 El siguiente paso consiste en establecer  las variables de entorno. Es necesario porque cuando se usa Java, Linux necesita saber dónde está ubicado el programa para ejecutarlo y qué versión de Java usar de forma predeterminada. Para modificar esto, usaremos el editor de texto nano. Primero, abra el archivo en Nano.

### Listar las versiones de OpenJDK instaladas

 Ejecuta el siguiente comando para verificar que se han descargado las diferentes versiones de OpenJDK.

```console
 ls /usr/lib/jvm
```



### Actualización de las variables de entorno

 Edita y modifica el fichero profile, con los comandos:

```console
sudo update-alternatives --config java
```
 y selecciona la version _8_.


<img src="ImagenesJDK/3.2.png" alt="3.2">

Vemos como se ejecutaron los comandos y modificamos las variables, como resultados tenemos la versión 8 de java. 



# Instalar Apache Maven con apt


 Instalar Maven en Ubuntu usando apt es un proceso simple y directo.

 Actualice el índice del paquete e instale Maven ingresando los siguientes comandos:

```
 sudo apt update
```
```
 sudo apt install maven
 
```

 <img src="ImagenesMaven/Maven 1.png" alt="Maven 1">
 
 Para verificar la instalación, ejecute mvn -version:
```
 mvn -version
```
<img src="ImagenesMaven/Maven 1.1.png" alt="Maven 1.1">

Comprobamos que tenemos el Maven instalado y la versión del mismo.  


### Instalar una versión concreta de Apache Maven

 En el momento de escribir este artículo, es la última versión de Apache Maven 3.8.2. Antes de continuar con el siguiente paso, visite la página de descarga de Maven para ver si hay una versión más nueva disponible.


 Descargue Apache Maven en el directorio /tmp:

```
wget https://www.apache.org/dist/maven/maven-3/3.8.2/binaries/apache-maven-3.8.2-bin.tar.gz -P /tmp
```


<img src="ImagenesMaven/Maven 2.png" alt="Maven 2">


 Una vez que se complete la descarga, extraiga el archivo en el directorio /opt
```
sudo tar xf /tmp/apache-maven-*.tar.gz -C /opt
```
 Para tener más control sobre las versiones y actualizaciones de Maven, que a crear un maven enlace simbólico que apunte al directorio de instalación de Maven:

```
sudo ln -s /opt/apache-maven-3.8.2 /opt/maven
```

<img src="ImagenesMaven/Maven 3.png" alt="Maven 3">


__Establecer variables de entorno__
 A continuación, necesitaremos establecer las variables de entorno. Para hacer esto, abra su editor de texto y cree un nuevo archivo llamado mavenenv.sh en el directorio /etc/profile.d/
```
sudo nano /etc/profile.d/maven.sh
```
Pega el siguiente código:

```
 export M2_HOME=/opt/maven
 export MAVEN_HOME=/opt/maven
 export PATH=${M2_HOME}/bin:${PATH}
```

 Guarde y cierre el archivo. Este script se utilizará al iniciar el shell.
 
 <img src="ImagenesMaven/Maven 4.png" alt="Maven 4">
 
 Ejecutamos el código anterior, guardamos y salimos. 

 
 Haga que el script sea ejecutable con chmod:

```
 sudo chmod +x /etc/profile.d/maven.sh
```
 Finalmente, cargue las variables de entorno usando el comando de source
```
 source /etc/profile.d/maven.sh
```

<img src="ImagenesMaven/Maven 5.png" alt="Maven 5">


__Verificar la instalación__

Para verificar que Maven está instalado, use el mvn -version que imprimirá la versión de Maven:

```
mvn -version
```

<img src="ImagenesMaven/Maven 5.png" alt="Maven 5">

Verificamos que Maven está instalado en la versión 3.8.2 
