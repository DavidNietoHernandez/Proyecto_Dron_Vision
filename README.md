# Proyecto_Dron_Vision
Repositorio con los códigos para configurar e instalar Gazebo, Git, PX4, QGroundControl, Python, MAVSDK y OpenCV. También se comparten algunos ejemplos para probar la instalación.

Para la realización de este proyecto se utiliza Ubuntu 22.04 LTS

1.- Instalación de Gazebo

Primeramente se inicia instalando el comando curl, el cual nos ayudará a verificar la conectividad a una URL y a transferir datos.

	sudo snap install curl

Gazebo es un software de simulación de robots de código abierto que permite probar y experimentar con robots en escenarios físicos simulados: 
-Simular robots y entornos en 3D 
-Crear escenarios realistas y complejos para probar y depurar aplicaciones ROS 
-Ver cómo interactúa el modelo robótico en un ambiente determinado 
-Verificar el funcionamiento de sensores, aptitudes de movilidad e incluso de superación de obstáculos 
-Observar cómo la gravedad afecta la estructura, caídas desde alturas determinadas, fricción, entre otras 

Gazebo se ejecuta en equipos Linux o equipos virtuales Linux. Se integra perfectamente con ROS (Robot Operating System), facilitando la transferencia de simulaciones a aplicaciones del mundo real. 

Entre sus características se encuentran: Realismo físico, Compatibilidad con ROS, Librería de modelos, Escalabilidad.

Una vez instalado la libreria del comando CURL, podemos ingresar a la página de Gazebo a través de terminal para descargar e instalar el software:

	 curl -sSL http://get.gazebosim.org | sh

2. Instalación de Git

Git es una herramienta de control de versiones que se utiliza para hacer seguimiento de los cambios en los archivos, especialmente cuando varios desarrolladores trabajan en los mismos archivos al mismo tiempo: 
-Permite a los desarrolladores trabajar de forma remota o sin conexión. 
-Permite a los desarrolladores realizar modificaciones en los archivos de forma independiente y segura. 
-Permite a Git fusionar los cambios de forma inteligente en la copia principal de los archivos. 
-Permite a Git realizar un seguimiento de los cambios de los desarrolladores, de modo que todos trabajen en la versión más actualizada del proyecto. 
-Es compatible con varios sistemas y protocolos. 
-Es eficiente para proyectos grandes y pequeños. 
-Es flexible para varios tipos de flujos de trabajo de desarrollo no lineal. 
-Está diseñado para conservar la integridad del código fuente gestionado. 

Git es un software de código abierto y gratuito. Se usa con más frecuencia en la programación de código, pero se puede usar con cualquier tipo de archivo.

En este caso instalaremos la herramienta para poder acceder al código de control de drones de PX4: 

	sudo apt install git

3.- Instalación PX4 Drone Autopilot

El siguiente repositorio contiene todo lo necesario para el control de drones con PX4. 

PX4 es un piloto automático de código abierto para drones que ofrece un estándar para el soporte de software y hardware para drones.

Iniciamos con la descarga del repositorio: 

	git clone https://github.com/PX4/PX4-Autopilot.git

Ingresamos a la carpeta donde se descargo:	

	 cd PX4-Autopilot

Y ejecutamoes el comando para crear la interfaz entre el kernel Linux y el usuario:   
	
 	bash ./Tools/setup/ubuntu.sh  # For Ubuntu

Una vez hecho esto, reiniciamos el equipo con el comando:

 	sudo reboot

Cuando se haya reiniciado el equipo regresamos a la carpeta donde se descargo:	

	cd PX4-Autopilot

y ejecutamos el siguiente comando para probar la instalación de gazebo y el software de PX4:

 	make px4_sitl gz_x500

4.-Instalación QGround Control

Ubuntu viene con un gestor de módem serie que interfiere con cualquier uso relacionado con la robótica de un puerto serie (o USB serie). 
Antes de instalar QGroundControl debe eliminar el gestor de módem y concederse permisos para acceder al puerto serie. 
También es necesario instalar GStreamer para soportar streaming de vídeo.

Antes de instalar QGroundControl por primera vez corra los siguientes comandos:

 	sudo usermod -a -G dialout $USER
	sudo apt-get remove modemmanager -y
	sudo apt install gstreamer1.0-plugins-bad gstreamer1.0-libav gstreamer1.0-gl -y
	sudo apt install libfuse2 -y
	sudo apt install libxcb-xinerama0 libxkbcommon-x11-0 libxcb-cursor-dev -y

Descargue el software de QGround Control de la siguiente liga:

 	https://d176tv9ibo4jno.cloudfront.net/latest/QGroundControl.AppImage

Instalé el software ejecutando el siguiente comando en la carpeta donde descargo el software

 	chmod +x ./QGroundControl.AppImage

Para correr el software lo puede hacer desde la terminal

 	./QGroundControl.AppImage

O dando doble click.

5.-Instalación de Python

Por lo general la instalación de Ubuntu ya viene con Python. Para verificar si contamos con Python corremos el siguiente comando:

	python3 --version

En caso de no tener Python instalado se ejecutarán los siguientes comandos:

	sudo apt update
	sudo apt install python3
	sudo apt install python3-pip

Este proyecto se ha desarrollado con Python 3.12, ya esta disponible 3.13 sin embargo, no lo he probado con dicha versión. En caso de tener una versión anterior al 3.12 actualizaremos Python con los siguientes comandos: 

	sudo apt install software-properties-common
	sudo add-apt-repository ppa:deadsnakes/ppa
	sudo apt update
	sudo apt install python3.12

6.- Instalación MAVSDK
MAVSDK es un conjunto de bibliotecas que permiten la interoperabilidad entre sistemas MAVLink y lenguajes de programación. Su objetivo es facilitar el uso de una API de alto nivel para MAVLink.

MAVSDK se puede utilizar en:
-Un dron, en un ordenador compañero
-En una estación terrestre o dispositivo móvil en tierra 

Algunas de las características de MAVSDK son: 
-Es multiplataforma, es decir, funciona en Linux, macOS, Windows, iOS y Android 
-Es rápido y ligero 
-Tiene una API simple que admite llamadas API sincrónicas y asincrónicas 
-Proporciona acceso programático a la información y telemetría del vehículo 
-Permite controlar misiones, movimiento y otras operaciones 

El proyecto MAVSDK está bajo la gobernanza de la Dronecode Foundation.

Para instalar dichas bibliotecas se ejecutará el siguiente comando: 

	pip install mavsdk

7.-Instalación OpenCV

OpenCV (Open Source Computer Vision Library) es una biblioteca de software de código abierto para visión artificial y aprendizaje automático. Se trata de una de las librerías más grandes del mundo en su campo y es utilizada por compañías, grupos de investigación y entidades gubernamentales. 

OpenCV ofrece una infraestructura común para aplicaciones de visión artificial y permite acelerar el uso de la percepción artificial en productos comerciales. 

Entre sus funciones se encuentran: Reconocimiento de caras, Identificación de objetos, Clasificación de acciones humanas en video, Seguimiento de objetos en movimiento, Reconstrucción 3D a partir de imágenes. 

OpenCV es multiplataforma y está disponible para los sistemas operativos GNU/Linux, Mac OS X, Windows y Android. Es compatible con varios lenguajes de programación, como Python, C++, y Java.
 
OpenCV es gratuito para uso comercial y académico.

Para instalar OpenCV en Ubuntu se ejecutarán los siguientes comandos:

	sudo apt update
	sudo apt install python3-opencv

8.-Ejemplos

Descargue los ejemplos ejecutando el siguiente comando:

	git clone https://github.com/DavidNietoHernandez/Proyecto_Dron_Vision.git

Para ejecutar los ejemplos y poder visualizar el dron en Gazebo y su movimiento en QGround Control ejecute los siguientes comandos en este orden:

8.1.-Abrimos Terminal Ctrl Alt T

8.2.-Abrimos Gazebo:

			cd PX4-Autopilot
			make px4_sitl gz_x500
8.3. En otra terminal abrimos la carpeta donde se encuentre QGroundControl y ejecutamos:

		cd  "Nombre de la carpeta"  
	        ./QGroundControl.AppImage
La otra opción sin usar terminal es ir directamente a la carpeta y dar doble click.
8.4.- Al abrir QGroundControl se escuchará una voz robótica y en la esquina superior izquierda se vera "Ready to fly"
8.5.-En otra Terminal acceder a la carpeta donde se guardaron los ejemplos en Python y ejecutar cualquier código:

	cd "Carpeta donde estan los ejemplos"
	python3 takeoff_and_land.py

 9.- Ejemplo Vision

 Para poder identificar algún objeto de un color especifíco se recomienda primero ejecutar el programa :

	python3 threshold_inRange.py

En la ventana que se abre se segmentaran los colores, a través del deslizamiento de las barras inferiores se debe oscurecer toda la pantalla dejando en blanco la figura del objeto que se quiere identificar. 

Una vez logrado, abres el código en Python de "track_and_follow2.py" y se apuntan los valores en la línea de código 235 y 236 en el orden en el que aparecen los LOW y los UPPER bounds.

 	HSV_LOWER_BOUND = (170, 115, 114)
        HSV_UPPER_BOUND = (180, 206, 255)

Este por ejemplo es para seguir una pelota naranja.
 
