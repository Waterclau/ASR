# Parte 1
## Paso 1: Crear una instancia de máquina virtual (VM) para el salto
Tras iniciar sesion en google cloud, navegamos a la sección VM instances y creamos dos instancias para este apartado. 
![image](https://github.com/Waterclau/ASR/assets/91564866/9ff77c1e-7caa-426e-9a92-57ef91115af5)
Como se puede ver en esta imagen , creamos una VM que utilizaremos como salto y otra llamada WEB que simulará la función del servidor web. 
En ambas máquinas ha sido necesario configurar la región, disco de arranque (con sistema Ubunto) y etiquetas que utilizaremos para asociar las reglas de firewall creadas a continuación.

##  Paso 2: Establecer las reglas de firewall
A continuación creamos dos reglas de firewall:
![image](https://github.com/Waterclau/ASR/assets/91564866/b4a830f5-7b37-4e41-864e-931ba765523e)
La primera se encarga de establecer una conexión segura entre nuestro pc y el servidor de salto.
![image](https://github.com/Waterclau/ASR/assets/91564866/7de02703-4165-498c-bb2c-0c682257e60a)
Mientras que la segunda se encarga de establecer una conexión segura entre el servidor de salto y el servidor web.
En cada una de estas reglas variamos las etiquetas y los rangos de ip necesarios para que se ajusten a las conexiones que queremos establecer en cada paso. 
En el de salto , es necesario añadir la ip de nuestro pc, mientras que en el del servidor web se debe añadir la ip interna del servidor de salto.

## Paso 3: Claves ssh

En este paso generaremos las claves SSH , las cuales son claves criptográficas compuestas por una clave privada y una clave pública, usadas para autentificar y cifrar la comunicación entre sistemas.

![image](https://github.com/Waterclau/ASR/assets/91564866/81cb7734-75fb-46c7-9146-6ef86a1ea739)

sdjkfskdf


ssh-keygen -t rsa -b 2048 -f "ruta\hacia\la\clave\id_rsa"


![image](https://github.com/Waterclau/ASR/assets/91564866/d73ee061-fddb-431f-98a1-b08a9405e5a7)

![image](https://github.com/Waterclau/ASR/assets/91564866/c674a5fe-f05d-463d-9fbe-05eaabce6766)

